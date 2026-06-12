---
title: "Missing text"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Syron on 2008-12-09
This is possibly one of the most annoying bugs I've ever seen. The text part of my window menus is gone. I first noticed this in Amarok, when I right-clicked on the icon the symbols for Previous track, Play, Pause, etc. were all there, but no text. Oddly enough the underscores were shown. Now I find that Open Office is doing the same thing! File, Edit, Help, all gone save for underscores. I'm stumped. 8.10 is fully updated, I've tried removing and adding both programs several times now, and for some reason those are the only two programs so far.

---

### Post by Tatty on 2008-12-09
Are you using any desktop effects?

Try running these applications from a terminal and see if you get any relevant error messages.

---

### Post by Syron on 2008-12-09
I thought it might have been desktop effects so I turned them off. I even tried switching to the on board graphics card but that did nothing.
Below is a screenshot of the missing text from a OpenOffice document recovery window.
[IMG]http://i178.photobucket.com/albums/w252/Ghostofgod/missingtext.png?t=1228859575[/IMG]

---

### Post by Michael.Godawski on 2008-12-09
hey Syron,

what is your graphic card? Found a similar post here:

[LIST]
[*][http://support.bibblelabs.com/webboard/viewtopic.php?t=11602&sid=361a690a525c41f17b3207316c8037f9](http://support.bibblelabs.com/webboard/viewtopic.php?t=11602&sid=361a690a525c41f17b3207316c8037f9)
[/LIST]
Also there the text in the application was missing but installing the 177 NVidia drivers solved this issue.

---

### Post by Syron on 2008-12-09
I'm running a GeForce2 MX 100/200 32 MB. But like I said I tried running it on the on board graphics card, which I'm about to try again.

---

### Post by Tatty on 2008-12-09
Try running the applications from a terminal to see if it outputs any error messages.

---

### Post by Syron on 2008-12-10
Ok, so to make my life easier I just dragged an open office icon onto my desktop and ran it. These are the results.

xxxx-desktop:~/Desktop$ . ooo-writed.desktop
bash: ooo-writed.desktop: No such file or directory
sam@sam-desktop:~/Desktop$ . ooo-writer.desktop
bash: [Desktop: command not found
bash: -writer: command not found
bash: Office: command not found
bash: WordProcessor: command not found
bash: application/rtf: No such file or directory
bash: application/vnd.ms-works: No such file or directory
bash: application/vnd.oasis.opendocument.text: No such file or directory
bash: application/vnd.oasis.opendocument.text-master: No such file or directory
bash: application/vnd.oasis.opendocument.text-template: No such file or directory
bash: application/vnd.stardivision.writer: No such file or directory
bash: application/vnd.stardivision.writer-global: No such file or directory
bash: application/vnd.sun.xml.writer: No such file or directory
bash: application/vnd.sun.xml.writer.global: No such file or directory
bash: application/vnd.sun.xml.writer.template: No such file or directory
bash: application/vnd.wordperfect: No such file or directory
bash: application/wordperfect: No such file or directory
bash: application/x-extension-txt: No such file or directory
bash: application/x-t602: No such file or directory
bash: text/plain: No such file or directory
bash: text/rtf: No such file or directory
bash: application/vnd.ms-word.document.macroEnabled.12: No such file or directory
bash: application/vnd.openxmlformats-officedocument.wordprocessingml.document: No such file or directory
bash: application/vnd.ms-word.template.macroEnabled.12: No such file or directory
bash: application/vnd.openxmlformats-officedocument.wordprocessingml.template: No such file or directory
bash: Word: command not found
bash: &#4640;&#4757;&#4896;&#4648;&#4837;: command not found
bash: &#2451;&#2527;&#2494;&#2480;&#2509;&#2465;: command not found
bash: de: command not found
bash: Yokuqhuba: command not found
bash: Ohlela: command not found
The program 'and' is currently not installed.  You can install it by typing:
sudo apt-get install and
bash: and: command not found
bash: &#4757;&#4853;&#4941;&#4963;: command not found
bash: &#1608;: command not found
bash: &#2480;&#2495;&#2474;&#2507;&#2480;&#2509;&#2463;,: command not found
The program 'i' is currently not installed.  You can install it by typing:
sudo apt-get install iprint
bash: i: command not found
bash: a: command not found
bash: und: command not found
bash: &#954;&#945;&#953;: command not found
The program 'and' is currently not installed.  You can install it by typing:
sudo apt-get install and
bash: and: command not found
bash: kaj: command not found
bash: y: command not found
bash: ja: command not found
bash: ja: command not found
syntax error. Last token seen: i
Garbled time
bash: et: command not found
bash: e: command not found
bash: ooo-writer.desktop: line 136: unexpected EOF while looking for matching `"'
bash: ooo-writer.desktop: line 157: syntax error: unexpected end of file

---

