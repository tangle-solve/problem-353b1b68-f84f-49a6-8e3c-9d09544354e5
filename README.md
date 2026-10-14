<!-- solve-problem:353b1b68-f84f-49a6-8e3c-9d09544354e5 -->
# Dürer’s edge-unfolding conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/353b1b68-f84f-49a6-8e3c-9d09544354e5).

## What is the problem?

Let P be a convex polyhedron with vertex set V, edge set E, and face set F. An **edge unfolding** is a spanning tree T of the 1-skeleton graph (V, E); cutting P along the edges of T and flattening the remaining surface into the plane yields a planar polygon called a **net**, together with a pattern of fold lines that refolds to P. The conjecture (attributed to Shephard, 1975, and popularized as Problem 9 in Demaine & O'Rourke's open-problems list, going back to Dürer's 1525 nets):

**Conjecture:** Every convex polyhedron has at least one edge unfolding whose resulting net is nonoverlapping (a single, simply connected planar polygon).

A counterexample would be a convex polyhedron for which *every* spanning tree of the edge graph, when flattened, produces at least two faces that overlap in the plane. Note the precise distinctions: (a) cuts must lie along polyhedron edges, not arbitrary surface cuts; (b) the net must be one connected piece; (c) self-overlap of the flattened surface is the failure mode, not crease ambiguity. General (non-edge) unfoldings are known to exist for every convex polyhedron — the open part is purely the restriction to the edge graph.

## Why does it matter?

A positive answer would guarantee that any convex polyhedral shape can be manufactured from a single flat sheet with cuts only along final fold edges — directly relevant to sheet-metal bending, packaging, origami engineering, and self-folding robotics. It is also the flagship open problem in unfolding theory, a testbed for techniques connecting Alexandrov-style intrinsic geometry to combinatorics of the edge graph. If false, understanding the obstruction would itself shape algorithms (all known practical heuristics assume nets exist).

## What's already known?

- **Every convex polyhedron has some (non-edge) nonoverlapping unfolding** (source-unfolding from any point, and the "blooming"/star-unfolding results; see O'Rourke's book, ch. 24–25). So the obstruction is specific to cutting only along edges.
- **Special classes verified:** all Platonic and Archimedean solids; prisms and antiprisms (always, via "zig-zag" paths); "nearly flat" polyhedra; nested "band-unfolding" results for prismatoids (O'Rourke); certain "dome" and terrain-like polyhedra.
- **Random/heuristic search:** computer search over spanning trees (maximizing cut length, or "peak/valley" heuristics) has found nonoverlapping nets on every polyhedron tried; no counterexample has ever been exhibited despite extensive search.
- **Cautionary result:** nonconvex polyhedra *can* fail badly — there exist orthogonal-box-like nonconvex polyhedra with no edge net (Biedl et al., "Unfolding some classes of orthogonal polyhedra", and subsequent counterexamples to the general nonconvex version by Bern et al.). Convexity is essential.
- **Key obstacle:** no invariant is known that controls whether a given spanning tree unfolds without overlap. Overlap depends on metric data (dihedral angles, face shapes) in a way that resists purely combinatorial arguments.

## What would count as solving it?

1. **Positive resolution:** a proof that for every convex polyhedron there exists a spanning tree of the edge graph whose flattening is nonoverlapping — ideally constructive, i.e., with a polynomial-time algorithm to find such a tree. A referee would need a rigorous nonoverlap argument, not just a heuristic.
2. **Negative resolution:** an explicit convex polyhedron plus a computer-assisted (or exact-arithmetic) proof that all spanning trees of its edge graph produce overlap. Careful handling of numerical rigor is required.
3. **Partial credit variants:** prove it for an infinite family not covered above (e.g., all simplicial polyhedra, all polyhedra of bounded face count), or prove that some natural heuristic (greedy longest-cut, "one-cut" methods) always works.

## How to start

1. Read O'Rourke, *How to Fold It* (2011), ch. 1–2, 6, and the survey chapter on unfoldings in Demaine–O'Rourke, *Geometric Folding Algorithms* (2007), ch. 22–25 — this is the definitive technical treatment.
2. Understand why the easy classes work: prisms via the top/bottom + lateral band argument; domes via angle-monotone paths. Ask what property of those arguments generalizes.
3. Study the candidate strategies in the literature: shortest-path-based trees, "steepest-edge" cuts, and O'Rourke's band unfoldings for prismatoids; identify where each proof breaks for general polyhedra.
4. If hunting a counterexample: focus on adversarial geometry (many nearly-coplanar faces, sharp spikes) where different tree choices force overlap; implement exact-precision overlap testing over all spanning trees for small edge graphs.

## Key references

- A. Dürer, *Underweysung der Messung* (1525). Historical origin: first printed polyhedron nets. Facsimiles/editions available; historical context only.
- G. C. Shephard, "Convex Polytopes with Convex Nets", *Mathematika* 22 (1975) 263–281. Frames the modern question of which convex polyhedra admit convex (and related nonoverlapping) nets.
- E. D. Demaine and J. O'Rourke, *Geometric Folding Algorithms: Linkages, Origami, Polyhedra*, Cambridge Univ. Press, 2007. Chapters 22–25 survey edge-unfolding, special classes, star/source unfoldings, and list this as open Problem 9 in its TOPP companion; see also cs.ulb.ac.be/~jozef/... no — see the authors' pages, e.g., https://erikdemaine.org/folding/ for the companion open-problems book *Folding and Unfolding in Computational Geometry* (2024), where this is Open Problem 9.
- J. O'Rourke, *How to Fold It: The Mathematics of Linkages, Origami, and Polyhedra*, Cambridge Univ. Press, 2011. Accessible entry point with the state of the art on unfolding.
- T. Biedl, M. Demaine, M. Demaine, A. Lubiw, J. O'Rourke, M. Overmars, J. Robbins, S. Whitesides, "Unfolding Some Classes of Orthogonal Polyhedra", *Comput. Geom.* 24 (2003) 39–54. Counterexamples for nonconvex polyhedra, delimiting where the conjecture can hold. (verify exact author list)
- J. O'Rourke, band-unfolding papers for prismatoids (~2001–2008), e.g., "Unfolding prismatoids as convex floor plans". (verify)

## Warnings

- **Do not confuse variants:** general cuts (source/star unfoldings) are solved; the open problem is *edge* cuts only. Also distinguish "no net exists" (overlap for every tree) from "a particular tree overlaps".
- Numerical experiments claiming counterexamples are notoriously error-prone due to floating-point overlap tests; any claimed counterexample needs exact arithmetic.
- The census's "related problems" cross-references (COMB-000187, ROBO-000001) appear to be duplicate records of this same conjecture — treat them as aliases, not distinct problems.
- Overlap is metric, not combinatorial: two polyhedra with the same edge graph can differ in unfoldability behavior, so pure graph-theoretic approaches are insufficient.
- Two citations above are marked "(verify)"; confirm exact bibliographic details before relying on them.

---
*`ALGO-000152` · unverified*

## Acceptance guidance

1. **Positive resolution:** a proof that for every convex polyhedron there exists a spanning tree of the edge graph whose flattening is nonoverlapping — ideally constructive, i.e., with a polynomial-time algorithm to find such a tree. A referee would need a rigorous nonoverlap argument, not just a heuristic.
2. **Negative resolution:** an explicit convex polyhedron plus a computer-assisted (or exact-arithmetic) proof that all spanning trees of its edge graph produce overlap. Careful handling of numerical rigor is required.
3. **Partial credit variants:** prove it for an infinite family not covered above (e.g., all simplicial polyhedra, all polyhedra of bounded face count), or prove that some natural heuristic (greedy longest-cut, "one-cut" methods) always works.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/353b1b68-f84f-49a6-8e3c-9d09544354e5?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000152.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000152)
