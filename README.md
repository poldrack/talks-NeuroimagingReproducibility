# talks-template

This is a talk template for Markdown-based presentations using Quarto.  

NOTE:  If you are not Russ Poldrack then you should first fork this repo and modify the files to replace my name and information with your own!

### Single Talk in its Own Repo (STOR) Template

This repository is built around the "Single talk in its Own Repo" (STOR) model.  Many researchers will give the same talk repeatedly over time, making changes with each presentation.  The STOR model maintains a single repository for that talk, with the main branch representing the current version of the talk.  

# Using the template

To create a new talk, simply use this repository as a template when you generate a new repository for the new talk. 

After creating the new repository, you will first need to make the following changes:

- You will need to enable Github Pages in order for the content to appear on the web.  To do this, go to `Settings -> Pages` in the new repository, and select "Deploy from a Branch" from the Source menu, select "Main" as the branch and "docs" as the folder, then click "Save".

- Set the version tag. The version tag of the current talk is set within the Makefile, e.g.:

`TAG = "NiPreps_BRAIN_11_17_2022"`

The scheme for the tag is `TalkName_Venue_Month_Day_Year`.  This tag is used to generate the PDF file, which is stored in `docs/pdfs` and is meant as the archival version of the talk.  The current talk is rendered in `docs/talk/talk.html` and is not stored for archival purposes (i.e. it is overwritten on each push). 

When the talk is completed, a new release should be generated on Github.  The tag used for this release *must* match the tag used in the Makefile in order for the PDF file to be found by the site building code.


### Organization

```
.
├── LICENSE.md              - license for repo (MIT)
├── Makefile                - Makefile to generate site
├── README.md
├── docs                    - Base for web site, automatically generated by Quarto
│   └── ...
├── site                    - Source files for web site
│   ├── _quarto.yml         - Config file for web site
│   ├── index.qmd           - Main qmd file for web site
│   └── styles.css          - CSS for web site
├── source                  - Home for source files
│   ├── README.md
│   └── ...
└── talk                    - Source files for talk
    ├── _quarto.yml         - Config file for talk
    ├── images              - Images to be included in talk
    │   └── ...
    ├── rp-theme.scss       - Slide theme (including CSS)
    └── talk.qmd            - Main source file for talk
```

### Usage

To build the entire project, including the talk (in both HTML and PDF formats) and the web site, use this command:

`make all`

The separate components can be built using the individual make commands in the Makefile.

Note that these commands will automatically push the content to Github; thus, you must have push access to the relevant repository.  This is designed for a single-user context; when multiple users are working on a project, it would be better to disable the git commands within Makefile and work in separate branches using [Github flow](https://docs.github.com/en/get-started/quickstart/github-flow).

