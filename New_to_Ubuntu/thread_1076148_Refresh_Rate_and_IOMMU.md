---
title: "Refresh Rate and IOMMU"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Rookie One on 2009-02-21
Okay, two questions.

1. What's the deal with my refresh rate in Linux. In the Screen Resolution window selecting 1280x960 the only choice I have is 51 Hz. In XP I could run 72 Hz at that resolution. It also lists my monitor as unknown. The NVIDIA X Server Settings tab recognizes my monitor, but the only two choices for 1280x960 are Auto and 60 Hz. How do I get my monitor to display 72 Hz in Linux?

2. When I boot up Ubuntu it says to enable IOMMU in BIOS. I looked and couldn't seem to find anything to do with IOMMU in my BIOS. What is IOMMU anyway? Is it important?

---

### Post by JerichoKru on 2009-02-21
IOMMU > [http://en.wikipedia.org/wiki/IOMMU](http://en.wikipedia.org/wiki/IOMMU)

You can try editing the /etc/X11/xorg.conf and change VertRefresh to the proper one.

---

