---
title: "Help - accidentally deleted folders inside  /etc/fonts"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by netlaptop on 2010-08-17
I accidentally deleted all stuff inside the folder /etc/fonts. I mean I deleted these folders and files: 

fonts.conf 
fonts.dtd
conf.d
conf.avail

Now the whole system fonts are very ugly :(( 

Is there anyway that I can restore the font configuration default setting of Ubuntu?

---

### Post by philinux on 2010-08-17
> **netlaptop said:**
> I accidentally deleted all stuff inside the folder /etc/fonts. I mean I deleted these folders and files: 

fonts.conf 
fonts.dtd
conf.d
conf.avail

Now the whole system fonts are very ugly :(( 

Is there anyway that I can restore the font configuration default setting of Ubuntu?

They should be in the trash as long as you haven't emptied it.

---

### Post by netlaptop on 2010-08-17
> **philinux said:**
> They should be in the trash as long as you haven't empties it.

I have permanently deleted all of them. I was trying to do some configurations for a non-Roman font, then I...

Hic hic hopefully there will be a solution...

---

### Post by netlaptop on 2010-08-17
I have just solved this by doing these steps:


I install fresh Ubuntu to a Virtual Machine. Then open the terminal:
> sudo nautilus


Then browse to /etc/fonts and copy all of those stuff to home user folder (~). Remember to change its permissions to let others can write and delete.

Then compress those folders and send to my email. Now open the email in the host OS. Then copy them to /etc/fonts by opening the terminal:
> sudo nautilus


Then sudo fc-cache -fv

Done! Sadhu x3!

---

### Post by gvij2000 on 2010-11-08
Thanks a lot.Saved me the trouble of reinstall.Your attachment is a life saver

best
vj

---

