# Optional historical AI — Faith and Frontier / Crown and Vesuvius

Faith and Frontier 4.5.53 and Crown and Vesuvius 0.17.28 remain separate submods. This release adds an optional historical policy layer to the current GFM/submod scripts. It is not an independent AI engine, a new map, or a guarantee of exact borders.

## Starting a campaign

In a new single-player 1830 or 1836 game, finish GFM's normal railroading questions. The new **Faith and Frontier: Historical AI Configuration** popup then offers **Enable Hyper-Realistic Historical AI** or **Use Normal GFM AI**, before returning to the existing setup sequence. The extended Choo-choo questionnaire also reaches this popup after its last question. The setting is saved globally in the campaign and cannot be silently changed by repeated setup dispatches.

Normal mode preserves the current GFM and both submods' pre-release outcomes, requirements and effects, including their existing historical weighting. It does not restore pristine upstream GFM. Existing saves without the new flag retain that normal behavior; this release does not edit saves or retroactively choose a mode. Multiplayer deliberately retains the existing setup because this engine/script path provides no verified host-authority test; another client cannot select a global policy through the new event.

Explicit railroading choices referenced by a reviewed chain take priority. Disabling colonial railroading also disables the new colonial preferences. The new mode never adds money, armies, factories, territorial cores or diplomatic influence as hidden AI bonuses.

## What changes when enabled

The reviewed registry contains 298 existing event choices. Of these, 293 receive conditional historical steering; five with a native base weight of zero remain unchanged. Within a reviewed date window, alternative options receive a zero AI weight only while the selected historical option is eligible under its existing zero-weight prerequisites. Human option weights are untouched. If the historical option is barred, the original choice weights remain in force. Applicable timed events receive a shorter mean-time-to-happen only under the same conditions; native event triggers remain in place.

Twenty-five existing decisions gain dated AI willingness. The mode suppresses their AI use before or after the reviewed window and increases willingness within it. Their normal territorial, financial, technological and diplomatic requirements still apply. Human decisions retain their original behavior. No decision is made affordable by a subsidy or executable despite a failed requirement.

Coverage includes Belgian independence, selected French and German political/diplomatic choices, German unification decisions, Italian unification and the authored Savoy chapters, the existing South African/Boer sequences, the Crimean War and Eastern Crisis, the Congress of Berlin, Romanian unification, Eastern Rumelia, the Bosnian annexation, selected colonial treaties and companies, Canada and Alaska, selected Latin American crises, Japanese reform and treaty choices, East Asian diplomacy, Indochina and Malaya, and Australasian developments. All entries, named choices, date windows and source filenames are listed in Historical-AI-Coverage.json. Coverage is explicit: unlisted events keep their existing AI.

## Balkan progression

The 1878 diplomatic sequence reuses GFM's Eastern Crisis, Congress and settlement events. It still needs their prerequisites, wars and diplomatic circumstances. The selected Ottoman settlement route avoids choosing the larger San Stefano alternative merely to paint the map.

Eastern Rumelia gains a narrowly gated peaceful union route during 1885–1889 when it and Bulgaria are AI-controlled, at peace, hold their required capitals, and have no foreign overlord beyond Ottoman suzerainty. The Ottoman ruler must also be AI-controlled and at peace. The existing decision/union effects execute the outcome. Player Rumelia, Bulgaria or Turkey cannot be absorbed through this added route.

An additional diplomatic request and reply recognize an existing royal Bulgaria's independence from Ottoman suzerainty from October 1908 through 1911. Bulgaria must already possess and control Sofia and Plovdiv; both governments must be AI-controlled and at peace. The reply rechecks the request before releasing the existing vassal relationship. It transfers no provinces, invents no Bulgarian state, and does not bypass another country's protectorate. If eligibility changes before the reply, recognition does not occur and an eligible AI can ask again later.

The Bosnian annexation decision receives its historical date window, followed by the existing 1912 Balkan League and war-settlement choices. The referenced Euratlas map covers the 1878–1912 interval before the Balkan Wars' final settlement; it should not be treated as a single postwar border snapshot. Actual battle outcomes, occupation and peace prerequisites remain consequential.

## Player intervention, divergence and limits

The policy works by changing eligible AI choices, not by repainting player conquests on an anniversary. Native effects of inherited GFM events are preserved; those events can still involve the player according to their existing rules. Reviewed triggered diplomatic choices that use FROM do not receive the extra preference when their sender is human. Balkan event steering additionally stands aside when one of the listed regional actors is human-controlled. This regional protection is deliberately conservative.

The 1900 world maps are historical targets for supported chains, not an exhaustive province-to-owner restoration table. No script guarantees an exact 1900 world or a 1912 Balkan map after major player intervention. Defeated or missing powers are not resurrected; wars are not automatically won; a human conquest is not undone by a new reconciliation event. Generic AI priorities, engine peace acceptance and military competence are not replaced. A statistical campaign success rate has not been measured.

The new Bulgarian recognition is a limited diplomatic abstraction. It does not model the entire Ottoman/Russian financial settlement or force a royal title change. Eastern Rumelia's merger retains GFM's existing consequences, including its Serbian reaction. These are stated limits, not undocumented promises of a flawless historical simulation.

## Artwork and historical references

The setup and recognition events use Anton von Werner's 1881 painting of the Congress of Berlin of 13 July 1878, in the public domain. The image was cropped and resized to the game's event format and encoded as DDS. It illustrates diplomacy; it is not represented as a painting of Bulgaria's 1908 proclamation.

- [Wikimedia Commons: artwork and original file](https://commons.wikimedia.org/wiki/File:Congress_of_Berlin,_13_July_1878,_by_Anton_von_Werner.jpg)
- [German History in Documents and Images: Congress painting](https://germanhistorydocs.org/en/forging-an-empire-bismarckian-germany-1866-1890/ghdi:image-1419)
- [Bulgarian government: history](https://gov.bg/index.php/en/About-Bulgaria/HISTORY/tabsss1)
- [Euratlas: Balkans 1878–1912](https://www.euratlas.net/history/hisatlas/balkan_states/191278BK.html)
- [GFM startup source referenced by the user](https://github.com/Historical-Expansion-Mod/Greater-Flavor-Mod/blob/master/GFM/events/CleanUp.txt)

The installed GFM scripts, the user's supplied proposals and annotated maps, and the existing authored chapters are the implementation references. The supplied text is treated as a design proposal; unsupported engine constructs and unmeasured percentage guarantees are not copied into runtime scripts.

## Compatibility and maintenance

GFM loads some files as whole-file replacements. Shared modified files are therefore mirrored byte-for-byte in both submods and their shared source store. This includes the startup event, so either overlay order reaches a working setup. Unique FF and CV content remains owned by its respective mod. Baseline GFM, the executable, performance loader, maps, province histories, population files, saves and map caches are not modified by this release.

Frozen pre-overlay sources live in work/historical-mode-source/files. The source registry names reviewed choices explicitly; it does not assume the first option is historical. Rebuild through `work/separate_submods.py --historical-mode-prepare`, and install a validated prepared result with `--historical-mode-only`. The builder verifies the hashes of its previous outputs before replacing them. If a subsequent content edit changes an overlaid file, update/rebase the frozen source deliberately rather than overwriting that edit. The legacy full rebuild is blocked after this layer is initialized because it contains older content versions.

Preparation verifies source equivalence with the mode off, date boundaries, human protection, explicit railroading precedence, native barred choices, both startup branches, repeated setup, multiplayer fallback, Rumelian and Bulgarian prerequisites, unique new IDs, localization, identical shared files, decision trigger structure and modifier references. Existing Italy 1871–1900 regression scenarios also run. Two unrelated inherited duplicate-ID groups are reported in the validation file and are unchanged by this release. DirectX validates the event texture independently of the game, archives are checked, and installation uses a recoverable backup and installed-file hash verification.

No in-game testing is performed, following the user's standing instruction recorded in work/AGENTS.md. Native scheduling, popup rendering, campaign balance and long-run map convergence remain unverified in the running game. Consult Historical-AI-Release.json for actual installation status.

## Steered event counts

- Americas: 26
- Asia: 16
- Balkans: 27
- Colonial: 27
- Europe: 26
- Italy: 94
- Oceania: 5
- Southern Africa: 72
