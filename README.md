# Dog Raglan Shirt Pattern Generator

A single web page that turns a dog's measurements into a raglan shirt pattern: back, front, sleeve,
collar, cuffs and hem trim. It is made for plotting on a paper roll, and it can also print on sheets.
Everything runs in the browser. There is no build step, no dependencies, and nothing is uploaded.

> This is a first-draft pattern. Make a test version in cheap stretch fabric before cutting good fabric.

## Contents
1. [Hosting](#hosting)
2. [What it makes](#what-it-makes)
3. [Inputs](#inputs)
4. [Pattern marks](#pattern-marks)
5. [Layout on the roll](#layout-on-the-roll)
6. [Output](#output)
7. [Checks and warnings](#checks-and-warnings)
8. [How the pattern is drafted](#how-the-pattern-is-drafted)
9. [Limits](#limits)

## Hosting
Upload `index.html` to a public GitHub repository, then open **Settings > Pages**, choose
**Deploy from a branch**, pick `main` and `/ (root)`, and save. The tool is live a minute later at
`https://<your-username>.github.io/<repository-name>/`. Any static host (Netlify, Cloudflare Pages,
GitLab Pages) works the same way. To update the tool, replace `index.html`.

## What it makes
| Piece | How many | Notes |
| --- | --- | --- |
| Back | 1, cut on the fold | Half piece with the fold on its left edge. Has the leash buttonhole mark. |
| Front | 1, cut on the fold | Half piece with the fold on its left edge. |
| Sleeve | 2, mirrored | Drawn once. Cut the second one flipped (fabric folded right sides together, or flip the pattern). |
| Collar | 1 | Rectangle folded in half lengthwise. Drawn as a half-length strip on a fold by default. |
| Sleeve cuff | 2 | Rectangle folded in half lengthwise. |
| Hem trim | 1 | Rectangle folded in half lengthwise, as long as the whole hem. Drawn as a half-length strip on a fold by default. |

## Inputs
All lengths can be entered in **inches or centimetres**. Switching units converts every value. A link
stores the numbers in inches, so it works whichever unit you used.

### Dog measurements
Measure the dog standing, at the widest point, with the tape snug but not tight.

| Field | Where to measure | Example |
| --- | --- | --- |
| Neck girth | Around the neck where the collar sits | 25 in |
| Chest girth | Widest part behind the front legs | 36 in |
| Front chest width | Across the front of the chest, between the front legs | 5.5 in |
| Back length | Base of neck to where the hem should end on the back | 16 in |
| Front length | Throat/chest to where the hem should end on the belly | 14 in |
| Neck to leg | Base of neck down to the armpit | 5 in |
| Upper leg girth | Around the upper front leg | 6 in |
| Sleeve length | Down the leg from the armpit. 0 gives leg holes only | 6 in |

### Fit and sewing
| Field | Default | Effect |
| --- | --- | --- |
| Body ease | 1.5 in | Extra room added around the body |
| Leg ease | 1.25 in | Extra room added around the leg |
| Seam allowance | 0.5 in | Added around every piece, except fold edges |
| Neck share: back | 48% | Share of the neck girth used by the back piece |
| Neck share: front | 24% | Share used by the front piece |
| Hem curve angle | 20 degrees | How steeply the hem curve meets the side seam |

The sleeve tops share what is left of the neck. With the defaults each sleeve top takes 14%.

### Collar, cuffs and hem trim
| Field | Default | Effect |
| --- | --- | --- |
| Collar height | 1.5 in | Finished height after folding in half. 0 leaves the collar out. |
| Cuff height | 1.5 in | Finished height after folding in half. 0 leaves the cuffs out. |
| Hem trim height | 1.5 in | Finished height after folding in half. 0 leaves the trim out. |
| Trim length (% of opening) | 100 | 100 makes each strip as long as the edge it joins. Use less for stretchy rib. |
| Draw the collar and hem trim as half pieces on a fold | on | Halves the length of the collar and hem trim in the layout. |

The cut height of a strip is twice the finished height plus the seam allowance on both long edges.

### Leash buttonhole
| Field | Default | Effect |
| --- | --- | --- |
| Add a leash buttonhole mark on the back fold | on | Turns the mark on or off |
| Distance from neck seam | 3 in | Down the back fold from the neck seam to the middle of the buttonhole |
| Buttonhole length | 1 in | Total length across the fold |

The back piece is a half, so the mark shows half the buttonhole: a short line from the fold with an
end tick. When the piece is cut on the fold it becomes the whole buttonhole.

### Layout and output
| Field | Default | Effect |
| --- | --- | --- |
| Paper roll width | 17 in | The layout is packed to fit this width. The roll length is continuous. |
| Show piece names | on | BACK, FRONT, SLEEVE, COLLAR and so on |
| Show instruction text | on | Cut counts, CUT ON FOLD, FOLD, BUTTONHOLE and the cut size of the strips |
| Sheet size | Letter | Letter or A4. Only used for "Print on sheets". |

### Buttons
- **Download PDF (exact size):** the layout as a vector PDF.
- **Download SVG:** the same layout as an SVG.
- **Print on sheets:** prints the layout in tiles on Letter or A4 paper.
- **Reset to example:** restores the example bulldog values and default options.
- **Copy link:** copies a link that holds all the numbers and tick boxes, so you can keep one link per dog.

## Pattern marks
- **Solid line:** the seam (sewing) line.
- **Dashed grey line:** the cutting line, which is the seam line plus the seam allowance. Fold edges have no allowance.
- **Notches:** one line marks the front seams and two lines mark the back seams. They sit in the middle of
  the raglan seam on the front piece and the back piece, and on the matching sleeve edge. Match single to
  single and double to double.
- **Fold symbol:** a bracket with arrows pointing at the fold edge. The words "CUT ON FOLD" can be turned off.
- **Grain lines:** double-headed arrows on the back, front and sleeve.
- **Fold line on strips:** a dash-dot line across the middle of each strip, where it folds in half lengthwise.
- **Buttonhole mark:** on the back fold, at the chosen distance from the neck seam.

The text can be turned off without losing any of these marks, apart from the words themselves.

## Layout on the roll
- The sheet is as wide as the roll width you enter, with a 0.5 in margin on each side and 0.5 in between pieces.
- The tool tries every order of the pieces. The collar, cuffs and hem trim can also be turned sideways.
  It keeps the shortest layout. The back, front and sleeve are never turned, so their grain lines stay
  true to the roll.
- If a piece is wider than the roll, the page tells you the width it needs and lays the pieces out at that width.
- Pieces that are placed sideways have their labels turned with them.

## Output
- **PDF:** one page, exactly the size of the layout, so the scale cannot change when a program opens it.
  Lines are vector paths with no fill colour, which suits a plotter. Text uses the standard Helvetica fonts.
  The page width equals the roll width you entered.
- **SVG:** the same drawing, with its width and height set in inches. Some programs resize an SVG when
  they open it, which is the reason the PDF is the safer file for plotting.
- **Sheets:** the layout is cut into Letter or A4 pages with a 0.5 in overlap, corner marks, and a 1 inch
  square on every page. Print at 100% (actual size) and check the square. Pages with no pattern on them are skipped.
- **Preview:** the page shows the layout with a light tint inside each piece. The tint is not in the PDF or SVG.

## Checks and warnings
The seam table lists lengths that must match when sewing: both raglan seams against the sleeve edges, the
two side seams, the sleeve underarm seams, the neck opening against the neck girth, and the length of each strip
against the opening it joins. The page also warns when:
- the front neck edge is wider than the front panel;
- the front length is longer than the back length;
- the back and front neck shares add up to 100% or more;
- the back or front length is shorter than the neck-to-leg measurement;
- the front panel is wider than the whole body;
- the trim length percentage is zero or less, or the roll is under 1.5 in wide;
- the leash buttonhole is too far down the back;
- the sleeve cannot be drafted with the current numbers (change the neck shares or the leg ease);
- a field is empty or negative.

## How the pattern is drafted
1. **Body:** the chest girth plus body ease is shared between the front panel (front chest width plus
   body ease) and the back piece, which takes the rest and wraps over the dog's sides.
2. **Neck:** the neck girth is split between the back, the front and the two sleeve tops.
3. **Raglan seams:** each runs from the neck edge to the armpit point, which sits at the neck-to-leg depth.
4. **Hem:** the side seam ends halfway between the back and front lengths. The hem is a curve from that
   point to the centre of the piece, where it reaches the full back or front length.
5. **Sleeve:** its two long edges are made exactly as long as the back and front raglan seams, and the
   cuff is as wide as the leg girth plus leg ease. The back edge is longer than the front edge, so the sleeve is lopsided on purpose.
6. **Strips:** the collar is as long as the neck opening, the cuff as wide as the sleeve cuff, and the hem trim
   as long as the whole hem, all measured along the sewing line and scaled by the trim length percentage.

## Limits
- This is a first-draft block. It has not been fitted on a dog, so use it for a test garment first.
- The collar is as long as the neck girth. It does not allow for the head going through, so check that on the test garment.
- Strip lengths are measured along the sewing line. Seam allowance for joining the ends is added in the cut size.
- The tool has no memory between visits. Use "Copy link" to keep a dog's numbers.
