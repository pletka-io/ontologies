# Pletka ontologies

The ontologies that [Pletka](https://pletka.io) projects use, as Pletka v2
modules. Each directory is one module, one per vocabulary prefix:

```
crm/
  ontology.yaml     prefix, namespace, title, family, the bases it requires, its source files
  src/              the RDF as the publisher released it
```

The module path is `github.com/pletka-io/ontologies/<prefix>`. A version is a
tag `<prefix>/v<version>`, for example `crm/v7.1.3`. One exception: the
module `sdo` has prefix `sdoe`, because the namespace table binds `sdo` to
`https://schema.org/`.

While this repository has no outside users, a tag may still move to fix a
module's metadata; the source RDF never changes under a tag. Once it has
outside users, tags never move and a fix gets a new version.

## Using a module

Require it in a project's `pletka.mod`; `pletka mod tidy` resolves the
closure (an extension brings in the base it requires) and writes `pletka.sum`.

```yaml
require:
  - {module: github.com/pletka-io/ontologies/crm, version: 7.1.3}
  - {module: github.com/pletka-io/ontologies/crmsci, version: "2.0"}
  - {module: github.com/pletka-io/ontologies/namespaces, version: "2"}
  - {module: github.com/pletka-io/ontologies/defaults, version: "1.3"}
```

`namespaces/` is the prefix table (prefix, namespace, aliases), itself a
module. `defaults/` declares the W3C basics (`dc`, `dcterms`, `owl`, `rdf`,
`rdfs`, `skos`, `xsd`).

## Modules

| Module | Versions | Namespace |
|---|---|---|
| `crm` (CIDOC CRM) | 6.2, 7.1.3 | `http://www.cidoc-crm.org/cidoc-crm/` |
| `crmarchaeo` | 1.4.1, 2.1.1 | `http://www.cidoc-crm.org/cidoc-crm/CRMarchaeo/` (1.4.1), `http://www.cidoc-crm.org/extensions/crmarchaeo/` (2.1.1) |
| `crmdig` | 3.2.1 | `http://www.ics.forth.gr/isl/CRMdig/` |
| `crmgeo` | 1.2.1 | `http://www.ics.forth.gr/isl/CRMgeo/` |
| `crminf` | 0.7 | `http://www.ics.forth.gr/isl/CRMinf/` |
| `crmpe` | 3.1.3 | `http://parthenos.d4science.org/CRMext/CRMpe.rdfs/` |
| `crmsci` | 1.2.6, 2.0 | `http://www.cidoc-crm.org/cidoc-crm/CRMsci/` (1.2.6), `http://www.cidoc-crm.org/extensions/crmsci/` (2.0) |
| `crmtex` | 2.0 | `http://www.cidoc-crm.org/extensions/crmtex/` |
| `crmsurv` | 1.0.2 | `https://github.com/takinsolutions/crmsurv/` |
| `crmaaa` | 1.5.4 | `https://takin.solutions/ontologies/crmaaa/` |
| `mahero` | 1.0 | `https://takin.solutions/ontologies/mahero/` |
| `aaao` | 2.2 | `https://ontology.swissartresearch.net/aaao/` |
| `admo` | 1.0 | `https://ontology.swissartresearch.net/admo/` |
| `cpro` | 2.0, 2.3 | `https://ontology.swissartresearch.net/cpro/` |
| `pwro` | 1.0 | `https://ontology.swissartresearch.net/pwro/` |
| `sari` | 1.0 | `http://w3id.org/sari#` |
| `globo` | 1.0 | `https://w3id.org/globalise/ontology/` |
| `lrmoo` | 1.0 | `http://iflastandards.info/ns/lrm/lrmoo/` |
| `frbroo` | 2.4 | `http://iflastandards.info/ns/fr/frbr/frbroo/` |
| `edm` (Europeana Data Model) | 1.0-extended | `http://www.europeana.eu/schemas/edm/` |
| `la` (Linked Art) | 0.9 | `https://linked.art/ns/terms/` |
| `la-addons` | 1.0 | `https://linked.art/ns/addons/` |
| `geo` (GeoSPARQL) | 1.0 | `http://www.opengis.net/ont/geosparql#` |
| `dln` (DLNarratives) | 2.0 | `https://dlnarratives.eu/ontology#` |
| `hdt` (Echoes HDT) | 1.1 | `http://isl.ics.forth.gr/ontology/echoes/` |
| `rdo` (Research Data Ontology) | 1.0 | `http://ontologies.mpiwg-berlin.mpg.de/rdo/` |
| `sdh` | 1.0 | `https://sdhss.org/ontology/core/1.0/` |
| `sdhso` | 1.0 | `https://sdhss.org/ontology/social-life/1.0/` |
| `spec` (RELEVEN) | 0.1 | `https://r11.eu/ns/spec/` |
| `so` (Similarity Ontology) | 0.1 | `https://r11.eu/ns/similarity/` |
| `nfdicore` | 3.0.0 | `https://nfdi.fiz-karlsruhe.de/ontology/` |
| `cto` | 3.0.0 | `https://nfdi4culture.de/ontology/` |
| `sdo` (NFDI4Culture schema extensions, prefix `sdoe`) | 0.2, 0.4 | `https://nfdi4culture.de/ontology/schema-extension#` |
| `knora-base` | 60 | `http://www.knora.org/ontology/knora-base#` |
| `dsm` (Knora standard models, flat) | 3 | `http://www.knora.org/ontology/standard-models#` |
| `defaults` (W3C basics) | 1.0, 1.3 | `https://pletka.io/ontologies/defaults/` |
| `namespaces` (prefix table) | 1, 2 | |

## Earlier bytes of a version

Some source files changed without a new version number. Each earlier state
is its own commit before the tagged one, so a project that used it can pin
it by commit id (a 40-hex selector instead of a version):

| Module | Version | Earlier commits, oldest first |
|---|---|---|
| `crmsurv` | 1.0.2 | `17ad22da32dd174ea455a596b13ba3fab3d25053` |
| `cto` | 3.0.0 | `c56b8943e3da1b318a7f52848504208fabb928a6`, `4a86b0983e3fb55d3697705ee766e366d2484896` |
| `defaults` | 1.3 | `2262a298434aa495669bd302c54c3793367fd26a`, `ebe9a2f701f0525ad6ae9412430c9a5508daf043`, `af949c0c2947e89a656722b8822283954e4d559e` |
| `nfdicore` | 3.0.0 | `b94e6a2598cb04ee73cdd21f0cbfc58608db823d`, `7795cedc5a088ad4f899026af5a164616a47c6ea`, `b7d11b37a245062a0f9b9943bcba4d9d8db2ac05`, `27b4032e7701d7234c24d6378f7bbafc95b3632f` |
| `sdo` | 0.4 | `e415fdca7003935506d9b3057ad5cbf76a14922b` (supersedes `ae30c155a7d9a87da8bece57fa4c7771b9a0d05a`, same bytes, prefix `sdo`) |

## Licences

The RDF under each `src/` is the publisher's and keeps the publisher's
licence. This repository adds the `ontology.yaml` metadata and the
namespace table.
