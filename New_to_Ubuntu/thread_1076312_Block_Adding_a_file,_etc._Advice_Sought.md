---
title: "Block: Adding a file, etc. Advice Sought"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Andavane on 2009-02-21
Hi
I find there is one place on which I get blocked again and again:

If I want to install something that's tricky (for me), I get the
instructions "add a line" or "change a line" to a file.

And I always fall down there.

I don't have a problem getting to the file, but you can't just change it.

I am determined to get past this block, and grapple with doing things this way, but the block is very stubborn.

I'm working through the lessons in [http://linuxcommand.org/](http://linuxcommand.org/) again.
perhaps something will click.

Anyone who feels this problem rings a bell, please add comment or help, as this is the one thing in Ubuntu which is proving to be quite a snag with me, perhaps as the result of years of working with windows.

Regards

John

PS: This block means I can't get my printer-scanner working because to do so means adding two lines, and I can't get programs (viz Moneydance)which used to run on an older distro to run on a newer one Intrepid). So every so often I need to boot into Windows.

IBM Thinkcentre.

main drive (windows XP)
DVD bay has hard drive with Intrepid;
Hardy on laptop (Sony vaio)

---

### Post by yeats on 2009-02-21
> If I want to install something that's tricky (for me), I get the
instructions "add a line" or "change a line" to a file.

And I always fall down there.

I don't have a problem getting to the file, but you can't just change it.

How are you accessing the file?  I'm assuming you're pointing and clicking via the graphical interface, right?  It sounds like you need to open the file with "sudo" prefixed to the command.  I'm using Kubuntu and haven't used Gnome in a while, but is there a command in the right-click (context) menu that says something like "Open Terminal here"?  If so, you can open the directory in the terminal and do

```
sudo gedit *filename*
```

which will open the file with "Administrator" (in Windows-speak) or root privileges.  Then any changes you make will be applied and will work.  I advise caution though! :-)  It is much easier to mess up configuration in Linux than in Windows.

---

### Post by Andavane on 2009-02-22
> **chrissharp123 said:**
> How are you accessing the file?  I'm assuming you're pointing and clicking via the graphical interface, right?  It sounds like you need to open the file with "sudo" prefixed to the command.  I'm using Kubuntu and haven't used Gnome in a while, but is there a command in the right-click (context) menu that says something like "Open Terminal here"?  If so, you can open the directory in the terminal and do

```
sudo gedit *filename*
```

which will open the file with "Administrator" (in Windows-speak) or root privileges.  Then any changes you make will be applied and will work.  I advise caution though! :-)  It is much easier to mess up configuration in Linux than in Windows.

Hi Chris,
>"How are you accessing the file?"
I was opening it by clicking through the graphics till I got there; however I realised that by getting in with permissions and altering the file that way, is NOT the thing to do ;)

As you say, it will be with 'sudo gedit', and going through the course of terminal again, things are beginning to fall into place. I feel that it will work out all right soon...

>" I advise caution though! :-) "
Indeed: I'd never do anything like that unless and until I thoroughly understood what I was doing. The only instance I'd do it was if it was from a site like brother, and their official driver/release, whatever.

I saw by the way that they had now updated their way of doing it in linux, so I'll see what the latest theory on it is.

Thanks very much by the way for going to the trouble of replying when you're not on gnome any more. I know it's a simple enough thing, but it's a thing which has proved a right sticking point with me, and I'm looking forward to moving beyond it.

Regards,

John

---

### Post by quinnten83 on 2009-02-22
If you want to click, you can open nautilus, the filebrowser as root.
```
gksudo nautilus
```
but again be careful.

---

### Post by Andavane on 2009-02-22
I see...

Well yes, as always, I'd do that, once I understood what was going on.

As a kid I used to love clocks and watches with glass so I could how it all worked inside.

I'm still tryng to form a kind of image of how Ubuntu works...
I saw how Windows works once, and it was  a right tangled mess... #-o

Cheers

---

### Post by Andavane on 2009-03-04
> **quinnten83 said:**
> If you want to click, you can open nautilus, the filebrowser as root.
```
gksudo nautilus
```
but again be careful.

That's how I did it in the end.
I went to the site required (Brother Solutions), made the alteration (noting the original), saved and exited the window, so root powers are closed.

Indeed. Being very careful.

It seemed ironic that all I had to do was to change two figures from "0664" to "0666".

Incredible what difference such a small   change can make.

Regards,

John

---

