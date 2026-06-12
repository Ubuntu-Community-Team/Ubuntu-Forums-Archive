---
title: "Wine font problem"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by photolinux on 2009-01-10
I have been having this problem with programs running in wine (image attached).

[[img]http://img185.imageshack.us/img185/2627/screenshotwineconfiguratj5.png[/img]](http://www.imagehosting.com/)

Any thoughts as to what is going on and how to fix it?

---

### Post by cwsnyder on 2009-01-10
This is a thought, maybe worthless, but did you try with Arial/Times Roman or one of the Windows TTF fonts instead of a Linux font?

---

### Post by Kellemora on 2009-01-10
Hi PL

Often when this occurs, users are finding TWO COPIES of the SAME FONT loaded in to usable places on their computers.

This happens when like you already had some fonts installed and then after the fact installed the mstcorefonts into a different folder.

In my case, I make SURE I have NO FONTS inside of the .wine/Drive_C/Windows/Fonts folder, it's completely EMPTY.

IF you have made a hidden fonts folder in your home directory, usually at /home/user/.fonts MOVE those fonts to /usr/share/fonts/truetype first.  

Now, go through ALL of your fonts, if you installed msttypefonts they will reside in their own folder.  It's OK to move them if you want to into the main fonts folder.

What you are looking for are two fonts that are the same FONT.
This can be TRICKY because you can NAME a font anything you want to.  Windows fonts are sometimes named using only numbers as the file name, sometimes abbreviations, sometimes by whole names.
Sometimes a font is loaded from a program you installed also!  It may be named MM86475.ttf and you already have brazio_7.ttf, which just happens to be the exact same FONT, just filed under a different name.
FWIW:  In Windows, this would CRASH the working Fonts folder!
In Linux, rather than a crash, you get EACH font being displayed, yet offset by a few pica's, at the same time.

This may NOT be what is causing your problem, as several others have experienced this problem and it was a double font issue, just the fact that a DEFAULT font was being used in place of the font that should be used.

And sorry, I don't remember right off hand which FILE does the substitutions anymore.  If you check some of the older posts, they may tell you.

Nonetheless, keep a sharp eye out for double fonts as it do cause problems!

TTUL
Gary

---

### Post by photolinux on 2009-01-18
> This is a thought, maybe worthless, but did you try with Arial/Times Roman or one of the Windows TTF fonts instead of a Linux font?
Is there a way to switch to different fonts in Wine? I have not found a font setting, perhaps because I am looking in the wrong place?



> Hi PL

Often when this occurs, users are finding TWO COPIES of the SAME FONT loaded in to usable places on their computers.

This happens when like you already had some fonts installed and then after the fact installed the mstcorefonts into a different folder.

In my case, I make SURE I have NO FONTS inside of the .wine/Drive_C/Windows/Fonts folder, it's completely EMPTY.

IF you have made a hidden fonts folder in your home directory, usually at /home/user/.fonts MOVE those fonts to /usr/share/fonts/truetype first.

Now, go through ALL of your fonts, if you installed msttypefonts they will reside in their own folder. It's OK to move them if you want to into the main fonts folder.

What you are looking for are two fonts that are the same FONT.
This can be TRICKY because you can NAME a font anything you want to. Windows fonts are sometimes named using only numbers as the file name, sometimes abbreviations, sometimes by whole names.
Sometimes a font is loaded from a program you installed also! It may be named MM86475.ttf and you already have brazio_7.ttf, which just happens to be the exact same FONT, just filed under a different name.
FWIW: In Windows, this would CRASH the working Fonts folder!
In Linux, rather than a crash, you get EACH font being displayed, yet offset by a few pica's, at the same time.

This may NOT be what is causing your problem, as several others have experienced this problem and it was a double font issue, just the fact that a DEFAULT font was being used in place of the font that should be used.

And sorry, I don't remember right off hand which FILE does the substitutions anymore. If you check some of the older posts, they may tell you.

Nonetheless, keep a sharp eye out for double fonts as it do cause problems!

TTUL
Gary 

I checked both  .wine/Drive_C/Windows/Fonts and /home/user/.fonts, and they are both empty. I do have msttypefonts installed.
    How would I proceed to check to see if double fonts are installed?

---

### Post by Kellemora on 2009-01-18
Hi PL

Inside the TrueType folder, there should be several fonts in there, plus you will have your folder for msttcorefonts.

You can download from Synaptic a tool called Font Viewer, this will let you see the REAL NAMES of the Fonts, not just the File name they are stored under.  

Also, there are a couple of other things that have been causing smeared fonts in Wine, so you may want to check out that too!

TTUL
Gary

---

### Post by photolinux on 2009-02-03
Here are all my fonts in truetype:

```
*@*-desktop:/usr/share/fonts/truetype$ ls /usr/share/fonts/truetype -r *
/usr/share/fonts/truetype:
uralic          ttf-indic-fonts-core  thai             kochi
unfonts         ttf-dejavu            openoffice       freefont
ttf-liberation  ttf-bitstream-vera    msttcorefonts    arphic
ttf-lao         ttf-arabeyes          latex-xft-fonts

uralic:
schou___.ttf  sansub__.ttf  romaui__.ttf  monou___.ttf  bookui__.ttf
schoui__.ttf  sansubi_.ttf  romaub__.ttf  gothu___.ttf  bookub__.ttf
schoub__.ttf  sanscu__.ttf  pallu___.ttf  gothub__.ttf
sansu___.ttf  sanscub_.ttf  pallui__.ttf  chanui__.ttf
sansui__.ttf  romau___.ttf  pallub__.ttf  booku___.ttf

unfonts:
UnDotum.ttf  UnDotumBold.ttf  UnBatang.ttf  UnBatangBold.ttf

ttf-liberation:
LiberationSerif-Regular.ttf     LiberationSans-Bold.ttf
LiberationSerif-Italic.ttf      LiberationSans-BoldItalic.ttf
LiberationSerif-Bold.ttf        LiberationMono-Regular.ttf
LiberationSerif-BoldItalic.ttf  LiberationMono-Italic.ttf
LiberationSans-Regular.ttf      LiberationMono-Bold.ttf
LiberationSans-Italic.ttf       LiberationMono-BoldItalic.ttf

ttf-lao:
Phetsarath_OT.ttf

ttf-indic-fonts-core:
Vemana.ttf      MuktiNarrow.ttf      Malige-b.ttf  lohit_hi.ttf
utkal.ttf       MuktiNarrowBold.ttf  lohit_ta.ttf  lohit_gu.ttf
Rachana_04.ttf  Malige-n.ttf         lohit_pa.ttf

ttf-dejavu:
DejaVuSerif.ttf       DejaVuSans.ttf      DejaVuSansMono-Bold.ttf
DejaVuSerif-Bold.ttf  DejaVuSansMono.ttf  DejaVuSans-Bold.ttf

ttf-bitstream-vera:
Vera.ttf    VeraSeBd.ttf  VeraMoIt.ttf  VeraMoBd.ttf  VeraBI.ttf
VeraSe.ttf  VeraMono.ttf  VeraMoBI.ttf  VeraIt.ttf    VeraBd.ttf

ttf-arabeyes:
ae_Tholoth.ttf       ae_Ostorah.ttf     ae_Japan.ttf     ae_Arab.ttf
ae_Tarablus.ttf      ae_Nice.ttf        ae_Hor.ttf       ae_AlYarmook.ttf
ae_Sindbad.ttf       ae_Nagham.ttf      ae_Haramain.ttf  ae_AlMothnna-Bold.ttf
ae_Sharjah.ttf       ae_Nada.ttf        ae_Hani.ttf      ae_AlMohanad.ttf
ae_Shado.ttf         ae_Metal.ttf       ae_Graph.ttf     ae_AlMateen-Bold.ttf
ae_Salem.ttf         ae_Mashq.ttf       ae_Granada.ttf   ae_AlManzomah.ttf
ae_Rehan.ttf         ae_Mashq-Bold.ttf  ae_Furat.ttf     ae_AlHor.ttf
ae_Rasheeq-Bold.ttf  ae_Khalid.ttf      ae_Electron.ttf  ae_AlBattar.ttf
ae_Petra.ttf         ae_Kayrawan.ttf    ae_Dimnah.ttf    ae_AlArabiya.ttf
ae_Ouhod-Bold.ttf    ae_Jet.ttf         ae_Cortoba.ttf

thai:
Waree.ttf                       Sawasdee.ttf
Waree-Oblique.ttf               SawasdeeOblique.ttf
Waree-Bold.ttf                  SawasdeeBold.ttf
Waree-BoldOblique.ttf           SawasdeeBoldOblique.ttf
Umpush.ttf                      Purisa.ttf
Umpush-Oblique.ttf              Norasi.ttf
Umpush-Light.ttf                Norasi-Oblique.ttf
Umpush-LightOblique.ttf         Norasi-Italic.ttf
Umpush-Bold.ttf                 Norasi-Bold.ttf
Umpush-BoldOblique.ttf          Norasi-BoldOblique.ttf
TlwgTypo.ttf                    Norasi-BoldItalic.ttf
TlwgTypo-Oblique.ttf            Loma.ttf
TlwgTypo-Bold.ttf               Loma-Oblique.ttf
TlwgTypo-BoldOblique.ttf        Loma-Bold.ttf
TlwgTypist.ttf                  Loma-BoldOblique.ttf
TlwgTypist-Oblique.ttf          Kinnari.ttf
TlwgTypist-Bold.ttf             Kinnari-Oblique.ttf
TlwgTypist-BoldOblique.ttf      Kinnari-Italic.ttf
TlwgTypewriter.ttf              Kinnari-Bold.ttf
TlwgTypewriter-Oblique.ttf      Kinnari-BoldOblique.ttf
TlwgTypewriter-Bold.ttf         Kinnari-BoldItalic.ttf
TlwgTypewriter-BoldOblique.ttf  Garuda.ttf
TlwgMono.ttf                    Garuda-Oblique.ttf
TlwgMono-Oblique.ttf            Garuda-Bold.ttf
TlwgMono-Bold.ttf               Garuda-BoldOblique.ttf
TlwgMono-BoldOblique.ttf

openoffice:
opens___.ttf

msttcorefonts:
Webdings.ttf                     georgia.ttf
webdings.ttf                     georgiai.ttf
verdanaz.ttf                     Georgia_Italic.ttf
Verdana.ttf                      georgiab.ttf
verdana.ttf                      Georgia_Bold.ttf
verdanai.ttf                     Georgia_Bold_Italic.ttf
Verdana_Italic.ttf               cour.ttf
verdanab.ttf                     couri.ttf
Verdana_Bold.ttf                 Courier_New.ttf
Verdana_Bold_Italic.ttf          Courier_New_Italic.ttf
trebuc.ttf                       Courier_New_Bold.ttf
trebucit.ttf                     Courier_New_Bold_Italic.ttf
Trebuchet_MS.ttf                 courbi.ttf
Trebuchet_MS_Italic.ttf          courbd.ttf
Trebuchet_MS_Bold.ttf            comic.ttf
Trebuchet_MS_Bold_Italic.ttf     Comic_Sans_MS.ttf
trebucbi.ttf                     Comic_Sans_MS_Bold.ttf
trebucbd.ttf                     comicbd.ttf
times.ttf                        ariblk.ttf
Times_New_Roman.ttf              Arial.ttf
Times_New_Roman_Italic.ttf       arial.ttf
Times_New_Roman_Bold.ttf         ariali.ttf
Times_New_Roman_Bold_Italic.ttf  Arial_Italic.ttf
timesi.ttf                       Arial_Bold.ttf
timesbi.ttf                      Arial_Bold_Italic.ttf
timesbd.ttf                      Arial_Black.ttf
Impact.ttf                       arialbi.ttf
impact.ttf                       arialbd.ttf
georgiaz.ttf                     andalemo.ttf
Georgia.ttf                      Andale_Mono.ttf


```




Does this information give any clues to my problem?

---

### Post by Gcottrell on 2009-02-03
I'm having the same problem with my wine installation. I can't even run the "Configure Wine" program. Mine shows no fonts at all, and some times garbled fonts.

---

### Post by 4Orbs on 2009-02-03
This fixed it for me.

ADD THIS code to your .wine user.reg file to fix font smearing of the wine configuration gui.

```
[Software\\Wine\\X11 Driver] 1227050429
"ClientSideWithRender"="N"
"DXGrab"="Y"
"Managed"="Y"
```

---

### Post by Gcottrell on 2009-02-04
> **4Orbs said:**
> This fixed it for me.

ADD THIS code to your .wine user.reg file to fix font smearing of the wine configuration gui.

```
[Software\\Wine\\X11 Driver] 1227050429
"ClientSideWithRender"="N"
"DXGrab"="Y"
"Managed"="Y"
```



I did that, and still had no luck,. I may delete my .wine folder, and start my windows program install over,. which I'm bummed about because I have WOW working, and the download install takes forever,.

---

### Post by photolinux on 2009-02-07
> I'm having the same problem with my wine installation. I can't even run the "Configure Wine" program. Mine shows no fonts at all, and some times garbled fonts.


Perhaps you could attach a screen shot?

> **4Orbs said:**
> This fixed it for me.

ADD THIS code to your .wine user.reg file to fix font smearing of the wine configuration gui.

```
[Software\\Wine\\X11 Driver] 1227050429
"ClientSideWithRender"="N"
"DXGrab"="Y"
"Managed"="Y"
```

This fixed it for me, thanks!

Thanks you everyone for your help!

---

### Post by bboston7 on 2009-02-07
Do you have an older nvidea card?  The old nvidea drivers are also known to cause that problem.  Try disableing the propriatary drivers.

---

### Post by keeneye on 2009-02-25
4Orbs...

Thanks for this - my Wine Configuration is now showing actual text.  Next step, configure my application.

Thanks!!
Ed

---

### Post by DaveRowell on 2009-04-12
Hey guy!  Thanks for the tip.  It seems to have made the difference - now I can see something!

Again thanks.

Dave Rowell

---

