---
title: "computer display &quot;out of frequency&quot; at Grub screen"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by TeamRiddle on 2011-06-24
When I'm loading my computer, which is dual booted with Ubuntu and vista, the screen that should be giving me the option of with OS to boot just makes my display say, "out of frequency". If i wait a couple minutes it loads into Ubuntu. 

And I've found out that it if hit arrow down and hit enter I can load safe mode (or something). The display is an HP w1907.

thanks for your help.

---

### Post by TerribleLIar on 2011-06-24
Try changing the resolution of Grub. In the terminal, run

```
sudo gedit /etc/default/grub
```Then find for the section that has the word resolution in it. The last line should read

```
#GRUB_GFXMODE=640x480
```Get rid of the comment (# symbol) to activate that line. 640x480 should be a resolution visible by any monitor. Finally, run

```
sudo update-grub
```And that should save your changes. It should be in range now. If not, I dunno.

---

### Post by Ozymandias_117 on 2011-06-24
Edit: Apparently I'm a slow typer. Just do what the person above me said. :)

---

