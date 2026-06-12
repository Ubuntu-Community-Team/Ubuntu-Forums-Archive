---
title: "opening .swf files firefox 3.5.5"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by alien8predator on 2009-12-17
I have been trying to open a .swf file link but each time the link to the file wouldn't play. I finally managed to install flash and each time I click on the link I get asked if I want to save it or open it with another software package. I just want it to play in firefox but I can't find a setting to reset firefox to default or undo this. I have searched around for a while. Can someone give me a pointer in the right direction?

---

### Post by teward on 2009-12-17
try to Drag the .swf file directly into your browser window.

---

### Post by mikewhatever on 2009-12-17
I didn't know installing flash was so hard, it's just point and click in Firefox. How about an example of a swf file or link or whatever you are trying to open?

---

### Post by sgosnell on 2009-12-17
Which flash did you install?  There are at least 3, I think.  You can get it straight from Adobe, or from the repositories.  I generally just give up and install from Adobe, and it works.

---

### Post by alien8predator on 2009-12-18
I installed flash using this example and it's working.

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

I'm was trying to open something like this.

[http://www.examplewebsite/ubuntu/cal.swf](http://www.examplewebsite/ubuntu/cal.swf)

Each time I opened it I couldn't click anything so then I tried install varies mediaplayer to try an open it by using the open remote url option. Before the example link above, I have to click on the link to get to it and then now firefox asks me if I want to download it or or to open it with whatever software package. It won't open as a flash file playing directly off of firefox. I want to view it directly from firefox, and being able to click on the the buttons in order to play it. I wasn't able to do this before I was able to view but not play it in firefox.

---

### Post by sgosnell on 2009-12-18
Go to [adobe.com](http://www.adobe.com/go/EN_US-H-GET-FLASH) and let it install the .deb for Ubuntu, through gdebi.  It should then autoplay in Firefox.

---

### Post by Cheesemill on 2009-12-18
Adobe don't make a Shockwave player for Linux, only a Flash player.

Edit - Ignore me, I thought .swf was a Shockwave format but it's Flash.

---

### Post by mybrownianmotion on 2009-12-29
I had this problem as well, and this is how I fixed it. First, close firefox. Open your .mozilla folder inside your home folder, open the firefox folder inside that, then open the folder inside that one, for me it was a bunch of random letters and numbers followed by .default, there was only one folder for me. Inside that folder find the file named mimeTypes.rdf, delete the file. start firefox, and if all goes well, local flash files should be working again.

---

