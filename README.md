# wesleyverhoeve-photography
Photography portfolio website

## Automated Gallery Configuration

This project uses an automated gallery configuration system to keep your galleries in sync with the images in your `/work` folders.

### How it works
- All image galleries are defined in `gallery-config.js` as arrays of image paths, one per gallery.
- The file `generate-gallery-config.js` is a Node.js script that scans all subfolders in `/work` and generates/updates `gallery-config.js` automatically.

### To update your galleries:
1. **Add or remove images** in any of the `/work` subfolders (e.g., `work/portraits I/`, `work/landing/`, etc.).
2. **Run the script:**
   ```sh
   node generate-gallery-config.js
   ```
   This will regenerate `gallery-config.js` to reflect the current images in each folder.
3. **Reload your site** in the browser. The galleries will now match the images in your folders.

### Notes
- The script supports `.jpg`, `.jpeg`, `.png`, `.webp`, and `.JPG` files.
- Gallery keys are generated from folder names (spaces become dashes, all lowercase).
- You can edit or extend the script for custom gallery logic if needed.

---

## Local Development / Preview

To preview your site locally, you can use a simple static server such as [http-server](https://www.npmjs.com/package/http-server):

1. **Install http-server** (if you haven't already):
   ```sh
   npm install -g http-server
   ```
2. **Start the server in your project root:**
   ```sh
   npx http-server . -p 8080
   ```
3. **Open your browser to:**
   [http://localhost:8080](http://localhost:8080)

This will serve your site so you can test all gallery and navigation features.

## POTENTIAL ASTRO SWITCH PLAN

This section outlines a step-by-step plan to migrate this static site to a dynamic Astro-based portfolio, optimized for a photographer and writer.

### 1. Initial Setup
- **Install Astro:**
  ```sh
  npm create astro@latest
  ```
  Follow the prompts (choose “empty” or “minimal” starter).
- **Move static assets:** Copy your `/work` folder (with all your images) into the new Astro project’s `/public` directory. Astro serves everything in `/public` at the root URL.
- **Copy your CSS:** Move your custom CSS into `/src/styles/global.css` (or similar) and import it in your layout or main entry file.

### 2. Dynamic Routing for Portfolios/Projects
- **File-based routing:** Create a file for each project/portfolio in `/src/pages/` (e.g., `thebestmedicine.astro` for `/thebestmedicine`).
- **Dynamic routes (optional):** Use `[slug].astro` for dynamic project pages and load data from a config or JSON.

### 3. Image Gallery Automation
- **Option A:** Keep your current workflow—add images to `/public/work/your-gallery/` and use a Node.js script to generate a JSON file with image lists. Astro reads this JSON to render galleries.
- **Option B:** Use Astro’s Content Collections or a custom integration to scan `/public/work/` folders at build time and generate image lists automatically. Just add images to folders and Astro will pick them up on the next build.

### 4. Clean URLs and SEO
- Astro pages are mapped to URLs automatically. Add metadata (title, description, Open Graph) in each `.astro` file for SEO and social sharing.

### 5. Full CSS Control
- Use global CSS, CSS modules, or Tailwind. Edit all CSS in Cursor as you do now.

### 6. Markdown/MDX for Writing
- Use Markdown or MDX files in `/src/content/` or `/src/pages/` for your writing. Astro renders Markdown as blog posts, essays, or project descriptions.

### 7. Deployment
- Deploy to Vercel, Netlify, Cloudflare, or any static host. Custom domains (like `www.wesley.co`) are easy to set up.

### 8. Example Directory Structure
```
/public
  /work
    /portraits I/
    /portraits II/
    /thebestmedicine/
    ...
/src
  /pages
    index.astro
    thebestmedicine.astro
    portraits-i.astro
    ...
  /components
    Gallery.astro
    ImageGrid.astro
    ...
  /styles
    global.css
/generate-gallery-config.js (optional, if you want to keep the script)
```

### 9. Step-by-Step Migration Plan
1. Set up Astro and move your static files and CSS.
2. Create a page for each portfolio/project.
3. Set up a gallery component that reads image lists from a JSON file or scans folders.
4. Add Markdown/MDX support for your writing.
5. Test locally, tweak CSS, and ensure everything works.
6. Deploy to your preferred host and set up your custom domain.

### 10. Resources
- [Astro Docs: Getting Started](https://docs.astro.build/en/getting-started/)
- [Astro Image Gallery Example](https://docs.astro.build/en/guides/images/)
- [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/)
- [Astro Markdown/MDX](https://docs.astro.build/en/guides/markdown-content/)

---

If you want a starter template or code sample for Astro, just ask!
