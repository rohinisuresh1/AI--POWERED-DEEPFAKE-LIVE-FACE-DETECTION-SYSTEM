# AI-POWERED DEEPFAKE LIVE FACE DETECTION SYSTEM

Here's a comprehensive visual explanation of the entire system — how it works from input to verdict. I'll draw this as two diagrams: first the overall pipeline, then the detailed signal analysis layer.That's the full end-to-end pipeline. Now here's a closer look at exactly how each of the three signal types catches different spoofing attacks — what they measure and which attack they defeat.Here's what both diagrams explain together:

<img width="1497" height="792" alt="image" src="https://github.com/user-attachments/assets/04e83e7f-e625-4490-9076-70a184bef560" />


**Diagram 1 — The pipeline** shows the full flow from raw webcam frames to a final binary verdict. The webcam feeds into face detection (landmark localisation), which feeds into three parallel analysis modules. All three converge into a CNN classifier that produces a liveness score. Anything above 0.5 grants access; below blocks it.


<img width="1497" height="878" alt="image" src="https://github.com/user-attachments/assets/8d8ccd55-2366-41eb-b87a-9f4dba27dd22" />


**Diagram 2 — Signal vs attack matrix** shows *why* you need multiple signals. No single signal defeats all three attack types:

- Skin texture analysis is the most universal — it catches photo, video, and mask spoofs because each leaves a distinct physical artifact (moiré patterns, screen reflections, or silicone surface with no pores).
- Retina tracking is strong against photos and video but only partial against 3D masks, which can have motorised eyes.
- Micro-motion catches photos (zero pixel variance) and masks (no breathing) but is harder to use against video since video inherently has motion.

The CNN fusion layer combines all six signals simultaneously, so even when one signal is fooled, the others compensate — that's what makes the system robust.

Click any box in the diagrams to ask a follow-up question about that specific component.
