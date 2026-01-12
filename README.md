# F5 Distributed Cloud Theme

A custom MkDocs Material theme for the F5 Distributed Cloud platform, providing Fortinet-branded styling, interactive features, and enhanced documentation capabilities.

## Overview

This theme extends the Material for MkDocs framework with:

- **Fortinet Brand Integration**: Official logos, colors, and styling
- **Interactive Pod IP System**: Dynamic IP replacement for lab environments
- **Custom Components**: Branded admonitions, navigation, and layouts
- **PDF Export**: Custom covers and styling for documentation exports
- **Enhanced Features**: Advanced markdown extensions and plugins

## Features

### Dynamic Pod IP Replacement

The theme includes a client-side system for replacing IP placeholders in documentation:

- **Persistent Storage**: Pod IPs stored in browser localStorage
- **Dynamic Updates**: Real-time replacement of `{{pod_ip}}` placeholders
- **Link Updates**: Automatic URL updates when IP changes
- **User Interface**: Clean form for IP input and management

### Brand Styling

- **Dual Logos**: Automatic light/dark mode logo switching
- **Color Scheme**: Fortinet red (#da291c) with Material Design integration
- **Typography**: Inter font for readability, Roboto Mono for code
- **Custom Admonitions**: Branded "forti" callout boxes

### Advanced Plugins

- **Content Management**: Awesome pages, literate navigation, include markdown
- **Interactive Elements**: Mark-as-read tracking, content tabs, asciinema player
- **Media Support**: Drawio diagrams, lightbox images, mermaid charts
- **Export Capabilities**: PDF generation with custom styling

## Configuration

### Environment Variables

The theme uses environment variables for flexible deployment:

```yaml
site_name: !ENV [MKDOCS_SITE_NAME, "Hands on Labs"]
site_url: !ENV [MKDOCS_SITE_URL, null]
repo_url: !ENV [MKDOCS_REPO_URL, null]
edit_uri: !ENV [MKDOCS_EDIT_URL, null]
```

### Theme Settings

Key configuration options in `mkdocs.yml`:

```yaml
theme:
  name: material
  custom_dir: docs/theme
  logo: theme/fabric.svg
  logo_dark: theme/fabric-white.svg
  features:
    - navigation.tabs
    - navigation.tabs.sticky
    - content.code.copy
    - content.action.edit
```

### PDF Export

Configurable PDF generation with custom branding:

```yaml
plugins:
  - exporter:
      formats:
        pdf:
          stylesheets:
            - docs/theme/covers/stylesheets/pdf.scss
          covers:
            front: docs/theme/covers/front.html.j2
```

## Usage

### In Documentation Projects

1. **Reference Theme**: Set `custom_dir: docs/theme` in your mkdocs.yml
2. **Include Assets**: Copy theme files to your docs/theme directory
3. **Configure Variables**: Set environment variables for site customization
4. **Enable Features**: Configure plugins and extensions as needed

### Pod IP Functionality

Add the form container to your markdown:

```html
<div id="pod-ip-form-container"></div>
```

Use placeholders in your content:

```markdown
Access your lab at: http://{{pod_ip}}:8080
```

### Custom Admonitions

Use the branded forti admonition:

```markdown
!!! forti "Important"
    This is a Fortinet-branded callout box.
```

## File Structure

```
theme/
├── mkdocs.yml              # Main theme configuration
├── custom.js               # Pod IP replacement functionality
├── extra.css               # Custom styling and brand colors
├── *.svg                   # Logo assets (light/dark variants)
├── favicon.ico             # Site favicon
├── partials/               # Custom HTML templates
│   ├── animation.html      # Animation components
│   ├── content.html        # Content layout
│   ├── header.html         # Custom header
│   └── tabs-*.html         # Navigation tabs
└── covers/                 # PDF export templates
    ├── front.html.j2       # PDF cover template
    └── stylesheets/        # PDF styling
```

## Development

### Testing Changes

```bash
# Serve documentation with live reload (from consuming repository)
mkdocs serve

# Build static site
mkdocs build

# Validate configuration
yamllint mkdocs.yml
```

### Customization

- **Styling**: Modify `extra.css` for visual changes
- **Functionality**: Update `custom.js` for interactive features
- **Layout**: Edit partials for structural changes
- **Configuration**: Adjust `mkdocs.yml` for plugin settings

## Integration

This theme is designed for the F5 Distributed Cloud ecosystem and integrates with:

- **GitOps Deployment**: Flux-managed documentation sites
- **Multi-Repository Structure**: Shared theme across documentation projects  
- **Container Builds**: Docker-based documentation generation
- **Automated Publishing**: CI/CD pipeline integration

## Brand Guidelines

### Logo Usage
- Use `fabric.svg` for light mode
- Use `fabric-white.svg` for dark mode
- Maintain aspect ratio and sizing

### Color Palette
- Primary: Fortinet Red (#da291c)
- Background: White/Black (auto-switching)
- Accent: Indigo for interactive elements

### Typography
- Body text: Inter font family
- Code blocks: Roboto Mono
- Maintain consistent hierarchy and spacing

## License

This theme is part of the F5 Distributed Cloud platform and follows Fortinet's brand guidelines and usage policies.