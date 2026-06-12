---
title: "WinImage - Is there an equivalent Linux application?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by cwmoser on 2009-01-18
VMware recommends that one use a Windows program called **WinImage** to create a bootable USB thumb drive by writing an *.dd file to it.

Is there an equivalent Linux application that can do the same thing?

Carl

---

### Post by clive littlewood on 2009-01-18
Hi

If you are trying to create a USB startup disc.

Go to System > Admin > create a USB startup disc   !!!!!!!!!   :)

Hope this helps

Clive

---

### Post by P3t3r on 2009-11-21
Still doesn't answer the question: is there an equivalent for WinImage? 

For example now I'd want to edit the contents of a given image, and I don't have windows available...

---

### Post by Georgia boy on 2009-11-21
Will this link help?

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

It is broken down into sections, Windows, Linux etc. Maybe something there? 

Maybe this link also. I did some searches in Ask.com.

[http://www.jamison.org/2008/02/03/making-a-usb-thumb-drive-linux-bootable/](http://www.jamison.org/2008/02/03/making-a-usb-thumb-drive-linux-bootable/)

Hopefully one of these might help. 

Tom

---

### Post by 3rdalbum on 2009-11-21
I think you can write the contents of a *.dd file by using the dd command...

---

### Post by Arup on 2009-11-21
Try ISO Master, its in synaptic.

---

### Post by Puzzled Guy on 2009-11-22
You can find out yourself:
1. Open Synaptic Package Manager
2. Click "Search"
3. Enter a description in the box (it's like Google, so pretend you're using Google!)
4. Wait for the results and search trough them.
5. If you don't like what you got, search again with different keywords.

One last thing. The packages that have the Ubuntu symbol next to them are supported (given updates) by Ubuntu/Canonical

---

### Post by greenfrog on 2009-11-22
imagewriter

---

### Post by frenchn00b on 2009-11-22
> **cwmoser said:**
> VMware recommends that one use a Windows program called **WinImage** to create a bootable USB thumb drive by writing an *.dd file to it.

Is there an equivalent Linux application that can do the same thing?

Carl

```
isomaster
dd 
mount -o iso9660
fusermount

```

---

### Post by P3t3r on 2009-12-06
> **3rdalbum said:**
> I think you can write the contents of a *.dd file by using the dd command...

Does this work for .vfd files? If yes that would be a solution, but how do I do that?

What I need to do is edit a file within a .vfd file. Help or solution would be greatly appreciated. :)

---

### Post by P3t3r on 2009-12-10
> **P3t3r said:**
> Does this work for .vfd files? If yes that would be a solution, but how do I do that?

What I need to do is edit a file within a .vfd file. Help or solution would be greatly appreciated. :)

Anyone?

---

