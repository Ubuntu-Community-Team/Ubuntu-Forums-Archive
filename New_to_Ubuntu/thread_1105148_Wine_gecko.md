---
title: "Wine_gecko"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Bastun on 2009-03-24
Hi,

I  have downloaded cabextract cos I am having trouble with the fonts in ies4linux that I have installed and I saw somewhere, someplace on my dismal wanderings around the Unix world that one needs certain Windows cabfiles to be extracted and installed in order to get to grips with Wine failings.
Unfortunately, I dont know cabfiles from a hole-in-the-wall. I understand that they are archives of useful files that can be extracted to SOMEPLACE in a unix env. Cabextract.org says as much and pointed me clearly to Ubuntu Linux (Feisty) cabextract package which I downloaded. Also  showed me how to use cabextract - man pages, options, the lot! Great. So, lets see what cab files I have on Ubuntu 8.10. A search turns up in /usr/share/wine/gecko a cab file wine_gecko-0.9.1.cab!!!!  Ah - that'll be the lad for me!! So I list whats in there using -l and it shows me all sorts of lovely wine-gecko files of all sorts. Now, I'm afraid, I'm flying blind!!! Where do I put these so they will be of use? They look to be useful for Wine , therefore might help in my forlorn attempt to get ise4linux running ok. Should they be extracted to some directory in the C drive?? I have no idea whatsoever. OK - I'll try to extract them where the cab file itself resides - just to see what happens.
So in: /usr/share/wine/gecko in run cabextract (no options) and I get this kind of guff:

wine_gecko/res/table-remove-row.gif: can't create file path
  extracting wine_gecko/res/ua.css
wine_gecko/res/ua.css: can't create file path
  extracting wine_gecko/res/viewsource.css
wine_gecko/res/viewsource.css: can't create file path
  extracting wine_gecko/res/wincharset.properties
wine_gecko/res/wincharset.properties: can't create file pat


I am at my wit's end with it all. I cannot find anywhere something that will tell me where precisely these files should be extracted to in order to be useful in the running of a particular Windows prog. Are ther files that I need to extract from a particular cab in order to fix ies4linux running in Wine? Where will I find the cab? What files within the cab might  be required? (The fonts in ies4linux are rubbish - see screenshot). Where do I install these files, if they exist?

I  would be very obliged to anyone who could assist here!!

Believe me - I am not stupid! I score somewhat above average in so-called IQ tests, for what that's worth. I am missing sdomething here. HELP

---

### Post by Panzor on 2009-03-24
You need to be a superuser to do pretty much anything past reading in any directory that isn't /home/.../   . Type "sudo" before the commands you're doing to get those outputs.

In my own wine experience, I've only had to get stuff in the "/home/<your username>/.wine/drive_c/windows/system32/" directory. [www.winehq.org](www.winehq.org) should have a page for your specified program with what to do if it doesn't work immediately perfect. Which is most if not all of them since sometimes some people have it work perfectly and others don't.

---

### Post by Bastun on 2009-03-24
Thanks for that! SUDO - how could I forget it!!! Muppet! ...and system32. Will give it a crack. Where's the Thanks and Resolved buttons?

Cheers,
bastun

---

### Post by Panzor on 2009-03-24
hey, no prob. Somehow I just stumbled across my own wine_gecko folder. It's right here: /home/max/.wine/drive_c/windows/gecko/0.1.0/wine_gecko

So that might be where you need to do all that stuff >_>.

---

