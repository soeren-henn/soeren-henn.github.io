# Updating the Research page

The Research page is built from two spreadsheets in the `_data` folder:

- `_data/papers.csv`: one row per paper or project
- `_data/coauthors.csv`: coauthor names and the website each name links to

You never need to edit HTML to add, change, reorder or remove a paper.

## To make a change

1. Open `_data/papers.csv` in Excel, Numbers or Google Sheets.
2. Edit, add or reorder rows. Within each section, papers appear in the same order as the rows.
3. Save it as CSV in UTF-8:
   - **Excel:** File > Save As > **CSV UTF-8 (Comma delimited)**. Plain "CSV" mangles accents and dashes, and the site will not build.
   - **Numbers:** File > Export To > CSV, with Text Encoding set to Unicode (UTF-8).
   - **Google Sheets:** File > Download > Comma-separated values, then replace the file.
4. Commit and push as usual. GitHub Pages rebuilds the site in a minute or two.

If a build fails, the live site stays as it was. The error appears under the repository's **Actions** tab on GitHub. The usual cause is a file saved as plain CSV instead of CSV UTF-8.

## Columns in papers.csv

| Column | What to put in it | Example |
|---|---|---|
| `section` | `Publication`, `Working paper` or `Work in progress` | `Working paper` |
| `hide` | Anything (such as `x`) to take the row off the site without deleting it | `x` |
| `title` | Paper title, without a final period | `The Local Memory of Repression and Who Fights` |
| `coauthors` | Names separated by semicolons. Spell them exactly as in `coauthors.csv` to get a link. Leave empty for solo papers. | `Gauthier Marchais; Raul Sanchez de la Sierra` |
| `year` | Publication year, shown in the left margin | `2024` |
| `status` | Shown before the journal name | `Forthcoming`, `Revise & resubmit`, `Under review` |
| `journal` | Journal name, shown in italics | `World Politics` |
| `citation` | Volume, issue and pages | `76(2):219–258` |
| `pdf` | Main link. The title and the "PDF" link point here. Use `/files/name.pdf` for a file in the `files` folder, or a full web address. | `/files/Henn_Chiefs.pdf` |
| `links` | Other links, written `Label \| address` and separated by semicolons | `NBER working paper \| https://www.nber.org/papers/w28631; Pre-analysis plan \| /files/PAP.pdf` |
| `replication` | Address of the replication archive (Dataverse, Zenodo, openICPSR...) | `https://doi.org/10.7910/DVN/X2JKHN` |
| `data` | Address that opens the data files (can be a filtered view of the archive, or a separate dataset) | |
| `code` | Address that opens the code files (or a GitHub repository) | |
| `replication_note` | Optional sentence shown under the replication links. `[text](address)` makes a link. | `Data and code are in a single package.` |
| `coverage` | Media coverage, in the same format as `links` | `VoxDev \| https://voxdev.org/...; Brookings \| https://...` |
| `award` | Award text, optionally followed by `\| address` | `Honorable mention, APCG Best Article Award 2023 \| https://...` |
| `abstract` | Plain text. Use `*asterisks*` for italics. Leave empty to hide the Abstract button. | |

Any cell can be left empty; the page simply leaves that line out.

## Replication materials (Data page)

Every row in the `Publication` section gets an entry under "Replication materials" on the Data page, and its entry on the Research page gets a "Replication" link that jumps there. A paper in another section gets an entry too as soon as one of its `replication`, `data` or `code` cells is filled in.

- Links that point to the same address are shown once, so pasting the archive address into all three cells shows a single "Replication archive" link.
- An entry with no links and no note reads "Replication materials are not posted yet."
- On Harvard Dataverse you can make a Data or Code link by filtering the archive's file list (for example by file type) and copying the address from the browser.

## Other changes

- **Rename a section heading:** edit the `sections` list at the top of `research/index.html`.
- **Add a coauthor link:** add a row to `_data/coauthors.csv` (name, website).
- **Add a new PDF:** put it in the `files` folder and enter `/files/filename.pdf` in the `pdf` column. File names are case-sensitive on the live site.
- **Email and profile links** (Google Scholar, GitHub and so on) are listed once in `_config.yml` and used on the home page and in the footer.
- **Google Analytics:** the measurement ID is the `google_analytics` line in `_config.yml`. Leave it empty to turn analytics off.
