---
title: "How To Clean Printer Heads"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by richie42 on 2009-01-24
I have a Epsom Stylus CX3810 and it needs a head cleaning, How do I do that?

PS:

I am a linux ultra n00b, so please be easy with instructions, thnks.

---

### Post by mrsudo on 2009-01-24
fortunately for you, cleaning printer heads would require absolutely ZERO linux experience.  

nothing could be of more help than a quick google search..

---

### Post by expatCM on 2009-01-24
Perhaps what richie42 is asking is whether or not there is an Ubuntu program that is used to clean the print heads.  I think Epson printers are bundle with Windows software which cleans the print heads ....  that may be the intended focus?

---

### Post by richie42 on 2009-02-05
Yeah that is... can I get an answr to this?

---

### Post by steveneddy on 2009-02-05
I did look on Google and noticed that there seems to be a lot of Linux software available for Epson printers.

Maybe this thread can steer you in the right direction.

[http://ubuntuforums.org/showthread.php?t=678881](http://ubuntuforums.org/showthread.php?t=678881)

---

### Post by richie42 on 2009-02-05
I dunno how to use this website though .... (I'm a Linux Newb)

---

### Post by steveneddy on 2009-02-05
> **richie42 said:**
> I dunno how to use this website though .... (I'm a Linux Newb)

What web site are you referring to?

Have you tried actually adding your printer?

Sometimes you can gain features by installing the printer and checking the settings in the Printing section:

System --> Administration --> Printing

EDIT:

From the Epson website:

[http://files.support.epson.com/htmldocs/cx38__/cx38__ug/wwhelp/wwhimpl/js/html/wwhelp.htm](http://files.support.epson.com/htmldocs/cx38__/cx38__ug/wwhelp/wwhimpl/js/html/wwhelp.htm)

There is a section on how to clean the print heads.

---

### Post by richie42 on 2009-02-08
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3810](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3810)

I dunno how to use this website

---

### Post by steveneddy on 2009-02-08
> **richie42 said:**
> I dunno how to use this website though .... (I'm a Linux Newb)

So while using Windows you never had to get on the internet?

You don't have to be familiar with Linux to be able to use the web.

What exactly do you not understand?

<edited>

[]("http://www.teachingideas.co.uk/welcome/")I gave you a link to a web site in a previous post that should give you instruction on how to get your printer to clean the print heads without a GUI on the PC.

---

### Post by richie42 on 2009-02-08
The Epsom website I CAN use. It is the other one. The thing with the epsom website is that a majority of the stuff that you need to do HAVE to be sone with the window... which I cannot access as this is Ubuntu.

I am starting to think that my ink is low...  I might buy some ink, replace it, and see what happens from there.

---

### Post by richie42 on 2009-02-09
No it is definately the printer. The heads need cleaned. How do I do that?

---

### Post by Shazaam on 2009-02-09
lsb-base version 3.2 is part of Intrepid if that is what you are confused about...
[http://packages.ubuntu.com/en/intrepid/lsb-base](http://packages.ubuntu.com/en/intrepid/lsb-base)
Linux drivers/apps usually don't come with a fully functional Microsoft Windows type configuration gui (graphical user interface) so you may be out of luck unless you can find/edit the files on your pc. From what I have read the software for HP printers is good but that knowledge doesn't help. If you can't clean the printer heads in linux look in your printer manual for instructions on how to do it at the printer. Also, you can access the cups configuration page by entering this in a web browser...
```
http://127.0.0.1:631/
```

Do you have any add/script blocking extensions installed in Firefox? Disable them/allow the website. If it says you aren't using a supported browser you can add an extension to Firefox that fools sites into thinking you are using IE. That can be found on the Mozilla/Firefox extensions/plugins pages.

---

### Post by steveneddy on 2009-02-10
> **richie42 said:**
> No it is definately the printer. The heads need cleaned. How do I do that?

Again, the link to the Epson website has instruction that will answer your question.

Here's the link again:

[http://files.support.epson.com/htmldocs/cx38__/cx38__ug/wwhelp/wwhimpl/js/html/wwhelp.htm](http://files.support.epson.com/htmldocs/cx38__/cx38__ug/wwhelp/wwhimpl/js/html/wwhelp.htm)

something about pressing a particular button on the printer itself and the heads will self clean.

Most all in one printers will have a utility onboard to clean the printer heads because in a corporate or business environment, where these are mostly used, other office employees won't have the printer suite on their PC, just the driver.

So they just walk up to the printer, touch the appropriate key or button and accomplish the task.

---

### Post by steveneddy on 2009-02-11
Something I just discovered about my HP printer:

It is on the network (not attached to any one computer) which I suppose your is, and I can type in the network address:

example - 192.168.1.2

and there is a "web page" that displays in my browser that gives me control on my various printer functions. One of which is

Clean Printer Heads

It's an option that you might try if your printer is connected VIA your network.

EDIT:

another cool address you can use to view your CUPS settings in your browser is:

[http://localhost:631/](http://localhost:631/)

You can control all of your printers, local and network, via this interface. You can also set user permissions so that your print jobs always get priority over someone else on the network.

Hope this helped.

---

### Post by philinux on 2009-02-11
> **richie42 said:**
> I have a Epsom Stylus CX3810 and it needs a head cleaning, How do I do that?

PS:

I am a linux ultra n00b, so please be easy with instructions, thnks.

Install mtink from synaptic. Run it from a terminal with 
```
gksu mtink
```

Get it Em Tea Ink

---

### Post by steveneddy on 2009-02-19
> **philinux said:**
> Get it Em Tea Ink

I don't get it.

---

