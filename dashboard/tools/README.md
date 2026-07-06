# DigitalForge Pro v1.0 Tools

**Location:** `src/tools/`  
**Purpose:** Core HTML tools to be embedded in Dashboard as Advanced tab  
**Status:** Ready for Week 2 integration

---

## TOOLS INCLUDED

### 1. DigitalForge_PromptGenerator.html (42 KB)
- **Purpose:** Generate detailed AI prompts for image creation
- **Features:** Customizable prompts, CSV export, Claude API integration
- **Model fallback:** Built-in (claude-opus-4-8 → claude-sonnet-4-6 → haiku)
- **Input:** Niche, collection, description, style
- **Output:** 10-50 unique prompts (CSV or text)

### 2. DigitalForge_ListingGenerator.html (68 KB)
- **Purpose:** Generate Etsy/Gumroad product listings
- **Features:** Title, description, tags, pricing suggestions
- **CSV Format:** Vela-compatible (10 fields, 13 tags max)
- **Model fallback:** Built-in fallback system
- **Input:** Prompts, niche, product count
- **Output:** Complete listings CSV (ready for Vela upload)

### 3. DigitalForge_PromptPlayer.html (26 KB)
- **Purpose:** Organize, edit, and manage prompts
- **Features:** Reorder, delete, combine, export organized prompts
- **CSV Support:** Upload/download CSV format
- **Use case:** Refine prompts before final use

### 4. DigitalForge_BatchScaler.html (61 KB)
- **Purpose:** Slice one master into every print size (6 ratios + square, both orientations) as JPG + PDF at 300 DPI, organized and zipped
- **Features:** Portrait/Landscape presets (US standard + ISO A-series)
- **Batch processing:** Upload ZIP, resize all at once
- **Output:** Organized ZIP with resized images by size
- **Sizes included:**
  - Portrait: 5x7, 8x10, 11x14, 12x16, 16x20 (US)
  - Portrait: A4, A3 (ISO)
  - Landscape: 7x5, 10x8, 14x11, 16x12, 20x16 (US)
  - Landscape: A4, A3 (ISO)

---

## WEEK 2 INTEGRATION PLAN

### How Dashboard Will Use These

**Dashboard Main Interface (Step 1-4):**
- User enters collection details
- Claude generates prompts + listings
- Download CSV

**Advanced Tab (Hidden by Default):**
- [PromptGenerator] — Full control mode
- [ListingGenerator] — Batch generation
- [PromptPlayer] — Organize existing prompts
- [BatchScaler] — Image resizing to every print size

### Technical Integration

1. **Embed as iframe or tabs**
   ```html
   <div id="advanced-tools">
     <div id="promptgen-tab"><!-- embedded tool --></div>
     <div id="listinggen-tab"><!-- embedded tool --></div>
     <div id="player-tab"><!-- embedded tool --></div>
     <div id="resize-tab"><!-- embedded tool --></div>
   </div>
   ```

2. **Shared API Key**
   - Dashboard passes API key to embedded tools
   - All tools use same Claude API credentials

3. **Shared State (Optional)**
   - If user generates in Dashboard, can refine in PromptPlayer
   - Prompts/listings flow between tools

---

## FILE STATUS

| File | Size | Status | Notes |
|------|------|--------|-------|
| DigitalForge_PromptGenerator.html | 42 KB | ✅ Ready | Model fallback system working |
| DigitalForge_ListingGenerator.html | 68 KB | ✅ Ready | Vela CSV spec implemented |
| DigitalForge_PromptPlayer.html | 26 KB | ✅ Ready | CSV import/export working |
| DigitalForge_BatchScaler.html | 61 KB | ✅ Ready | All ratios + square, 300 DPI |

**Total:** 270 KB of functional v1.0 tools

---

## IMPORTANT NOTES FOR WEEK 2

### API Key Handling
- Each tool embeds Claude API calls
- Dashboard should handle API key management
- Consider: Shared key storage, rate limiting

### CSV Specifications
- **ListingGenerator output:** Must match Vela spec (10 fields, 13 tags)
- **PromptPlayer input/output:** CSV format (prompts only)
- **BatchScaler:** Outputs JPG + PDF per size, organized into a ZIP

### Testing Requirements
- Tools work in isolation ✅ (already tested v1.0)
- Tools work when embedded in Dashboard (needs testing Week 2)
- API key properly passed to embedded tools
- No conflicts between simultaneous tool use

---

## VERSION NOTES

**v1.0 Tools Status:**
- PromptGenerator: Model fallback working, recent update (June 2)
- ListingGenerator: Recent updates for CSV spec validation
- PromptPlayer: CSV import/export, stable
- BatchScaler: All ratios + square configured, 300 DPI verified

**Known Issues:**
- None blocking for integration

**Ready for embedding in Dashboard.** ✅

---

## DURING WEEK 2 DEVELOPMENT

1. **Build Dashboard main page** (4-5 hrs)
   - 4-step wizard flow
   - Generate button
   - Download buttons

2. **Create Advanced tab** (2-3 hrs)
   - Embed these 4 tools
   - Set up API key sharing
   - Test tool access

3. **Polish & test** (2-3 hrs)
   - Responsive layout (desktop only)
   - Error handling
   - Full workflow testing

---

These tools are production-ready and waiting to be embedded. ✅
