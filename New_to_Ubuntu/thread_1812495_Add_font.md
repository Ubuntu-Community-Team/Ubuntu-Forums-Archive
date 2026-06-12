---
title: "Add font"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by hdanap on 2011-07-26
Hi, 

I just downloaded this font i wanted to add to inkscape "http://sandeen.net/GnuMICR/download/" after downloading it, i have no clue what to do.

Help please Anybody

Thanks

---

### Post by Anuovis on 2011-07-26
Depends on the format but I think you can double click the downloaded font file and there should be a button to install. Worked for me many times.

I peeked into the link and it seems everything is tar.gz archives. That is like zip or rar you probably saw in Windows. Right click on tar.gz and choose to extract it. 

The fonts inside seem to be a bit complicated than what I've used myself but there is also an instruction file on how to add them, try that.

---

### Post by Paddy Landau on 2011-07-26
To add a font for yourself only, try double-click in Nautilus and select Install Font. If that doesn't work, try adding it to the directory [FONT=Courier New]~/.fonts[/FONT] and then log out and in again.

To add a font for everyone, add it to the directory [FONT=Courier New]/usr/share/fonts[/FONT] and then log out and in again.

Instead of logging in and out, you can close all relevant windows and enter the commands:
```
fc-cache -f
sudo fc-cache -f
```

---

### Post by hdanap on 2011-07-26
> **Paddy Landau said:**
> To add a font for yourself only, try double-click in Nautilus and select Install Font. If that doesn't work, try adding it to the directory [FONT=Courier New]~/.fonts[/FONT] and then log out and in again.

To add a font for everyone, add it to the directory [FONT=Courier New]/usr/share/fonts[/FONT] and then log out and in again.

Instead of logging in and out, you can close all relevant windows and enter the commands:
```
fc-cache -f
sudo fc-cache -f
```


Solved, Thanks a bunch m8

---

