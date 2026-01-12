# Toronto Neighborhood Vibes - Development Plan

## Vision
Create vibe-aware neighborhood profiles for 2ronto.ca that capture the *feel* of each area, not just amenities.

---

## Part 1: Data Sources - What Exists

### Primary Sources (Rich Vibe Content)
- [ ] **BlogTO Neighbourhoods** - https://www.blogto.com/neighbourhoods/
  - Has guides for every major neighborhood
  - Includes local business listings, restaurant reviews
  - Community-contributed content with authentic voice

- [ ] **Toronto Life Neighbourhood Crawl** - https://torontolife.com/tag/neighbourhoods/
  - Celebrity/local-guided walking tours
  - Personal narratives about neighborhood character
  - Hidden gem recommendations

- [ ] **Spacing Magazine** - https://spacing.ca/toronto/
  - Urban design perspective
  - Public realm focus (parks, streetscapes)
  - Jane Jacobs-style urbanism lens

### Secondary Sources (Useful but Less Vibes)
- [ ] Moving2Canada - newcomer perspectives
- [ ] Destination Toronto - tourism angle
- [ ] Fox Marin / Real Estate blogs - market trends, demographics
- [ ] Reddit r/toronto, r/askTO - community discussions

### Image Sources
- [ ] Google Street View (systematic capture)
- [ ] Instagram geotags (#kensington, #thebeaches, etc.)
- [ ] Flickr Toronto groups
- [ ] Personal photography walks

---

## Part 2: Vibe Engine Analysis

### Current Capability (Text Only)
The Vibe Engine processes text using sentence embeddings and outputs 22 dimensions:

| Dimension Group | Attributes |
|----------------|------------|
| Temporal | pace, rhythm, density |
| Energy | intensity, flow, stability |
| Emotional | valence, arousal, intimacy |
| Conceptual | abstraction, temporality, complexity |
| Spatial | openness, geometry, depth |
| Cultural | historicity, specificity, subculture |
| Sensory | texture, brightness, warmth, color |

### Can It Assess Images? Not Yet, But...

**Option A: Vision Extension (Build It)**
- Add CLIP or OpenCLIP embeddings
- Create multimodal vibe network
- Train on image-vibe pairs
- Complexity: Medium-High, 2-3 weeks

**Option B: LLM Preprocessing (Use Claude)**
- Use Claude's vision to describe neighborhood images
- Feed descriptions to existing Vibe Engine
- "Describe the vibe of this street scene"
- Complexity: Low, immediate

**Option C: Hybrid Approach (Best)**
- Collect text descriptions from blogs
- Use Claude to generate vibe descriptions from photos
- Combine both through Vibe Engine
- Cross-validate human-written vs AI-described

**Recommendation: Start with Option B/C**
- Fastest to prototype
- Validates concept before building vision model
- Can collect training data for eventual Option A

---

## Part 3: Implementation Plan

### Phase 1: Data Collection (Week 1)
- [ ] Scrape BlogTO neighborhood pages (ethical, respect robots.txt)
- [ ] Extract Toronto Life Neighbourhood Crawl articles
- [ ] Collect 5-10 representative photos per neighborhood
- [ ] Compile into structured dataset

### Phase 2: Text Vibe Analysis (Week 2)
- [ ] Process all neighborhood descriptions through Vibe Engine
- [ ] Generate vibe profiles for each neighborhood
- [ ] Identify vibe clusters (which neighborhoods feel similar?)
- [ ] Create "vibe signature" for each area

### Phase 3: Image Vibe Analysis (Week 3)
- [ ] Use Claude vision to describe neighborhood photos
- [ ] Feed descriptions to Vibe Engine
- [ ] Compare image-derived vibes vs text-derived vibes
- [ ] Identify gaps/inconsistencies

### Phase 4: Integration into 2ronto.ca (Week 4)
- [ ] Design neighborhood profile template
- [ ] Add vibe visualization (radar charts?)
- [ ] Create "neighborhood matcher" tool
- [ ] Write human-readable vibe descriptions

---

## Part 4: Neighborhood Vibe Framework

### Proposed Vibe Categories for Toronto
Based on Vibe Engine dimensions, adapted for neighborhoods:

**Energy Vibe**
- Buzzing/Chill
- 24-hour/9-to-5/Sleepy
- Tourist-heavy/Local-only

**Cultural Vibe**
- Established/Emerging/Transitioning
- Homogeneous/Diverse/Mixed
- Mainstream/Subcultural/Counter-cultural

**Aesthetic Vibe**
- Historic/Modern/Mixed
- Polished/Gritty/Natural
- Dense urban/Village-feel/Suburban

**Social Vibe**
- Family-oriented/Young professional/Student/Mixed
- Community-tight/Anonymous/Transient
- Wealthy/Working-class/Mixed-income

### Sample Neighborhood Profiles

**Kensington Market** (hypothetical)
```
Energy: 7/10 - Bustling but human-paced
Cultural: 9/10 subcultural - Bohemian, anti-establishment
Aesthetic: 8/10 gritty - Colorful chaos, vintage shops
Social: High community, diverse, mixed-income
Signature: "Organized chaos with a beating heart"
```

**Financial District** (hypothetical)
```
Energy: 9/10 weekdays, 2/10 weekends
Cultural: 4/10 mainstream - Corporate, transactional
Aesthetic: 9/10 polished - Glass towers, suits
Social: Anonymous, professional, wealthy
Signature: "Money moves here, then leaves"
```

---

## Part 5: Future Vision

### Interactive Features
- [ ] "Find My Vibe" quiz - match user to neighborhoods
- [ ] Vibe comparison tool - side-by-side neighborhoods
- [ ] Vibe timeline - how neighborhoods have changed
- [ ] "Vibe walk" routes - experience multiple vibes in one walk

### Data Enrichment
- [ ] Night vs day vibe differences
- [ ] Seasonal vibe changes (summer vs winter)
- [ ] Micro-neighborhood variations (north vs south end)
- [ ] Transit accessibility impact on vibe

### Community Features
- [ ] User-submitted vibe reports
- [ ] "Vibe of the week" from different neighborhoods
- [ ] Local business vibe tags
- [ ] Event vibe predictions

---

## Part 6: Technical Architecture

### Data Pipeline
```
Sources → Scraper → Raw Data → Vibe Engine → Vibe Profiles → 2ronto.ca
                        ↑
                  Claude Vision
                  (for images)
```

### Storage
- Neighborhood text corpus (SQLite or JSON)
- Image collection (local or cloud)
- Vibe profiles (JSON with 22 dimensions)
- User-generated vibe data (future)

### API Design
```
GET /api/neighborhoods
GET /api/neighborhoods/{name}/vibe
GET /api/neighborhoods/match?vibe=artistic,chill
GET /api/vibe-compare?a=kensington&b=yorkville
```

---

## Immediate Next Steps

1. [ ] **Research**: Deep-dive into BlogTO and Toronto Life content structure
2. [ ] **Prototype**: Pick 3 diverse neighborhoods (Kensington, Yorkville, Leslieville)
3. [ ] **Test**: Run their descriptions through Vibe Engine
4. [ ] **Validate**: Do the vibe outputs match human intuition?
5. [ ] **Iterate**: Refine approach based on results

---

## Questions to Explore

- How granular should neighborhood boundaries be?
- How to handle neighborhoods in transition (gentrification)?
- Should we weight local voices higher than visitor reviews?
- How to present vibe data without stereotyping?
- Can we create a "vibe distance" metric between neighborhoods?

---

## Resources

### Major Publications
- BlogTO Neighbourhoods: https://www.blogto.com/neighbourhoods/
- Toronto Life Neighbourhood Crawl: https://torontolife.com/culture/most-popular-neighbourhood-tours-of-2025/
- Spacing Toronto: https://spacing.ca/toronto/
- **The Local** (award-winning nonprofit): https://thelocal.to/
  - In-depth neighborhood-level journalism
  - Won CJF Jackman Award for "Divided City" life expectancy analysis
  - Quarterly issues on housing, transit, climate, urban health

### Toronto Substacks & Newsletters

**Urban/City Politics:**
- **City Hall Watcher** (Matt Elliott): https://cityhallwatcher.substack.com/
  - Toronto city hall deep dives, former Metro writer
- **Chris Spoke's Newsletter**: https://chrisspoke.substack.com/
  - Housing policy, missing middle, development
- **Next Metro**: https://nextmetro.substack.com/
  - Urban structure, transit, density analysis
- **Challenger City TO**: https://challengercities.substack.com/
  - Podcast/newsletter on Toronto's urban future

**Food & Neighborhoods:**
- **Taste Buds (TasteToronto)**: https://tastetoronto.substack.com/
  - Toronto's biggest food newsletter, neighborhood dining guides
- **Antotastes**: https://antotastes.substack.com/
  - Independent restaurant reviews, critical takes

### Key Writers to Follow
- **Shawn Micallef** - Toronto Star columnist, Spacing co-founder, author of *Stroll* and *Frontier City*
- **Suresh Doss** - CBC/Star, covers Toronto's full culinary breadth
- **Matt Elliott** - City Hall Watcher, Toronto politics
- **Chris Spoke** - Housing policy advocate, Missing Middle Summit organizer
- **The Local team** - Tai Huynh (EIC), Nicholas Hune-Brown

### Other Resources
- Moving2Canada Guide: https://moving2canada.com/planning/destination-guides/toronto/
- Destination Toronto: https://www.destinationtoronto.com/the-6ix/neighbourhood-guides/
- Time Out Coolest Neighbourhoods 2025: https://www.blogto.com/city/2025/09/toronto-neighbourhood-worlds-coolest-2025/
