---
title: "Conky: if_empty = Segmentation fault"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by FearlessPc on 2008-12-30
Hi

My Conky was running great until i added this line
```
${if_empty ${mpd_title}}No title${endif}
```
i get "Segmentation fault" .

If i remove that line everything is ok.

I checked all the other if_*'s they are all closed with ${endif}.

Any idea ?

---

