---
title: "Terminal Font"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by littlewontons on 2010-01-26
Hi,

I just downgraded from Karmic to Hardy and noticed that the terminal font looks odd in Hardy. The bold words are very condensed and hard to read. I am currently learning terminal and would like to see if there is a fix. I've checked the fonts for the terminal in Karmic using
```
fc-match monospace
```
and saw that it was DejaVu Sans Mono, which is also the same in Hardy. But the rendering of both fonts look different. Could someone help me with this?

---

### Post by byStanderone on 2010-01-26
...here's a nice thread for you to try:
[http://ubuntuforums.org/showthread.php?t=780946](http://ubuntuforums.org/showthread.php?t=780946)

---

### Post by littlewontons on 2010-01-26
I have already tried that .fonts.conf file. It improves the Terminal slightly, but bold fonts are still very condensed. After using the .fonts.conf, it actually made all my other settings uncrisp. The rest of the fonts outside of Terminal, were very jagged.

---

### Post by 311005901 on 2010-01-26
littlewontons, go to System>Preferences>Appearance and click on the "Fonts" tab. Make sure you have the correct rendering method selected. (Mine's set on Subpixel Smoothing.)

---

### Post by littlewontons on 2010-01-26
Yup. Its currently set at Subpixel Smoothing. I am not too sure what is going on. At first I thought it was different versions of the fonts in Karmic vs Hardy, but then the fonts rendered to be the same.

---

### Post by littlewontons on 2010-03-04
No body out there knows how to fix this? I'm surprised that this didn't irritate others because it makes the bold font hard to read.

---

### Post by byStanderone on 2010-03-05
...perhaps the attention is now on lucid, and maybe, others haven't encountered your font problem...i myself haven't come across such predicament since gutsy.

---

### Post by mcduck on 2010-03-05
You need to set the correct DPI value for the resolution you use and your monitor's physical size. With wrong DPI value your fonts will always be rendered badly,evne more so with subpixel smoothing.

System/Preferecnes/Advanced, Fonts-tab and click the "Details"-button. And here's a DPI calculator you can use to get the correct value: [http://members.ping.de/~sven/dpi.html]("http://members.ping.de/~sven/dpi.html")

---

### Post by byStanderone on 2010-03-05
...thanks mcduck, but can't find the advance menu bar under system>preferences in my karmic install...seems it's not a default bar? am just a bit curious bout it.

---

### Post by mechro on 2010-03-05
It's **System > Preferences > _Appearance_ > Fonts: Details button** or right-click empty space on your Desktop and select **Change Desktop Background**.

---

### Post by byStanderone on 2010-03-06
hi mechro,

i think mcduck is talking of a different setting, cause he mentioned something about dpi...and it is under system>preferences>advance, i don't have it on my install.

---

### Post by mechro on 2010-03-06
> **byStanderone said:**
> hi mechro,

i think mcduck is talking of a different setting, cause he mentioned something about dpi...and it is under system>preferences>advance, i don't have it on my install.

As far as I know there isn't an "Advanced" menu item. As I said, to get to the dpi setting go to...

**System > Preferences > Appearance > Fonts: Details button**

---

### Post by byStanderone on 2010-03-06
haha...thanks mechro, so that's it 'dots per inch', found it!

---

