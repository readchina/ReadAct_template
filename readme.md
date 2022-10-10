# ReadAct_template

[![CI](https://github.com/readchina/ReadAct_template/actions/workflows/ci.yml/badge.svg)](https://github.com/readchina/ReadAct_template/actions/workflows/ci.yml)

This templates provides an empty copy of [ReadAct](https://github.com/readchina/ReadAct) for those interessted in extending its approach to their own data set. The template allows for much greater freedom during development compared to the traditional model of collaborting via forks. 

For more information, please consult ReadAct's [documentation](https://readchina.github.io/readact.html).

## Usage

You can create an empty database that follows ReadActs data-model for you to work with by clicking on the <span style="color:green">green</span> `Use this template` button. Afterwards, follow the prompts and give your new database a name. Out of the box, your database will be configured to follow [ReadAct's]() data model. That means a set of tables, table schemas, and pre-configured views, as well as the continous intergration configuration and automation we use for validation, data transformations, e.g. to `tei-xml`, and data enrichment via wikidata. 

Should you wish to expand the pre-configured data model, you need to adjust:

1. The csv files inside `/csv/data/`.
2. The accompanying table schemas inside `/csv/schema/`.
3. The `xquery` transformations inside `/xml/modules`.
4. The metadata files such as `datapackage.json` and optionally `data-dictionary.csv`.

By default, CI is configured to cross-reference your entries with those already part of ReadAct to avoid data-duplication, and to maintain compatibility. That means that IDs and entities already part of ReadAct will raise an error on CI if they are reassigned. 

<!-- TODO(DP): How to turn this off -->

### Adjust

To complete the set-up of your database. You'll need to provide the title of your database and replace the template name `readact_template` in two places:
-  [`datapackage.json`](https://github.com/readchina/ReadAct/blob/c1c52beaf20b8eb5469cd7ff55a1260b84b96b18/csv/datapackage.json#L4).
-  [`tei_header.xml`](https://github.com/readchina/ReadAct_template/blob/a1662aa94b66730602fc3b468ffa2db53ab019dd/xml/tei_header.xml#L9)

You also need to supply your author's name within the same two files:
-  [`datapackage.json`](https://github.com/readchina/ReadAct/blob/c1c52beaf20b8eb5469cd7ff55a1260b84b96b18/csv/datapackage.json#L9).
- [`tei_header.xml`](https://github.com/readchina/ReadAct_template/blob/a1662aa94b66730602fc3b468ffa2db53ab019dd/xml/tei_header.xml#L10)

Lastly, all views in `datapackage.json`  are using the URL of the template repo: `/readchina/ReadAct_template/main/`. To actually have them feature your own data must replace them with the URL of your repo, e.g.: [here](https://github.com/readchina/ReadAct_template/blob/main/csv/datapackage.json#L204)

```json
"data": {
    "url": "https://raw.githubusercontent.com/readchina/ReadAct_template/main/csv/views/view01a_txt-titles.csv"
}
```

We also recommend to insert your own 'DOI' as soon as it is available where appropriate, and to update the markdown pill at the top of this file that points to the CI of the template repo, so that it points to your new repo.

## Requirements for local development

-  Python: `>=3.8`
- [frictionless-py](https://github.com/frictionlessdata/frictionless-py)
- [ReadActor](https://github.com/readchina/ReadActor) (*helper module*)
- [daff](https://github.com/paulfitz/daff)(*for better csv diffing*)
- [basex](https://basex.org) (*testing only*)
- [textql](https://github.com/dinedal/textql) (*testing only*)

Provided you have python installed, run:

`pip install ReadActor pandas frictionless csvkit daff`

## New Contributors

New contributors should consult these [guidelines](.github/contributing.md)
Please check the [wiki](https://github.com/readchina/ReadAct/wiki) for general how-to's, FAQ, and to learn about best practices.
