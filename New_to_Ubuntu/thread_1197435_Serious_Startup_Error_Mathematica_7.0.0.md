---
title: "Serious Startup Error Mathematica 7.0.0"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Extragalactic on 2009-06-26
Hello people, 

I upgraded from Ubuntu 8.04 to Ubuntu 9.04. At the beginning Mathematica had a problem (ParametricPlot3D didn't show the plot) and now it won't start. It gives me a window titled 'Serious Startup Version' and tells me my Mathematica version might be corrupted.

Any ideas?

---

### Post by alphacrucis2 on 2009-06-26
> **Extragalactic said:**
> Hello people, 

I upgraded from Ubuntu 8.04 to Ubuntu 9.04. At the beginning Mathematica had a problem (ParametricPlot3D didn't show the plot) and now it won't start. It gives me a window titled 'Serious Startup Version' and tells me my Mathematica version might be corrupted.

Any ideas?

Perhaps 9.04 includes libraries that aren't compatible with your version of Mathematica. Have you tried Mathematica support. It's commercial software after all.

---

### Post by Ruth Lazkoz on 2009-07-17
Hi,

I have experienced the same error after and automatic update in 9.04, or maybe after another problem I was not concious of. 

I reinstalled mathematica and it did not work, but I found a fix that worked for me. I removed the .mathematica (or .Mathematica) hidden file in my home directory and it worked. Don't ask me why but it did. 

Still waiting for a reply from Wolfram, fortunately I discovered this workaround earlier.

Best luck,

Ruth

---

