---
title: "Upgrade from 9.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by donescamillo on 2010-05-01
I dont even know why I bother to do it but anyway..

I had 9.10 working on a dual boot system. It had its little problems, but it worked at least. I downloaded 10.04, checked MD5 sum (diligent that I am), burnt a disk etc. When it booted I got a screen with scrambled graphics, ie I could not discern anything. Clearly a problem with the display driver.
If I have 9.10 and do update via the update manager will I end up with a 10.04 system?
If I try to install Kubuntu will I have the same problem, ie is the display driver the same? Probably is...

regards,
donescamillo

ps it is very frustrating when old problems dont get fixed and new ones (particularly in areas where it worked) are introduced.

---

### Post by zvacet on 2010-05-02
> If I have 9.10 and do update via the update manager will I end up with a 10.04 system?
Yes!

It look like you have problem with graphic driver.Type in terminal

```
lspci | grep VGA
```

and post output here.Probably somebody will take it from there and help you to install right driver.

---

