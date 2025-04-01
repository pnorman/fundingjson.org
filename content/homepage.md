+++
+++

funding.json is a manifest that enables Free and Open Source Software (FOSS) projects to declare their financial needs in a machine-readable format. The self-contained JSON file can be easily published in repositories or websites, functioning similarly to robots.txt or Progressive Web App manifests.

By making funding requirements publicly crawlable and indexable, funding.json makes aims to bring discoverablity to FOSS projects, helping connect those seeking financial support with potential backers.


## Schema

Current version is v1.0.0

```json
{{ read_file(path="static/static/funding.schema.json") }}
```
<a href="#" data-copy-clipboard>Copy</a>

-----------

## Example

Assuming that the manifest is located at `https://example.com/funding.json`
```json
{{ read_file(path="static/static/funding.example.json") }}
```
<a href="#" data-copy-clipboard>Copy</a>

<br />

For repository hosting platforms like GitHub, the manifest can be checked into the project repository directly, eg: `https://github.com/example/coolapp/blob/main/funding.json`

-----------

### wellKnown

If the manifest references URLs, such as a project's webpage, that are not on the same domain as the `funding.json` manifest itself, then the `wellKnown` URL must point to a `/.well-known/funding-manifest-urls` file.

This file must contain the URL of the `funding.json` manifest URLs that reference it. The file can contain multiple URLs, one per line. This establishes provenance and verifies that that the publisher of the manifest is authorised to solicit funding on behalf of the URLs (entity, projects) described in the manifest. This follows the [.well-known](https://en.wikipedia.org/wiki/Well-known_URI) convention. An example scenario is described below.

|                                                 |                                                              |
| ------------------------------------------------|--------------------------------------------------------------|
| Manifest location                               | https://example.com/funding.json                             |
| Project URL referenced in the manifest          | https://my-cool-project.net                                  |
| Expected `wellKnown` along with the project URL | https://my-cool-project.net/.well-known/funding-manifest-urls |
| Contents of the `wellKnown` file                | `https://example.com/funding.json`                           |

### tags

While the `tags[]` field under projects is meant for arbitrary lowercase-alphanumeric-dash strings to describe the projects, [project-tags.txt](/static/project-tags.txt) can be used as a reference list for uniformity.

-----------

## Tools

- [FLOSS/fund open directory](https://dir.floss.fund)
- [Live manifest validator](https://dir.floss.fund/validate)
- [Manifest builder UI](https://vishnukvmd.github.io/funding.json/)
