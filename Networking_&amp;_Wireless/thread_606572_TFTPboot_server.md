---
title: "TFTPboot server"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-11-08
Hey Forum ..

Just for knowing what options I have. 

I work at a company which uses both Linux and Windows - we have well - pretty many employee's which messes up their PC  sometimes. 

Then I would like to make an install server instead of finding the CD each times - and ending up with missing the drivers etc - So is it possible to make an server that have both the linux PXE boot image and one for Windows ?? (is that working the same way as in Linux ??? ) 

So you'll be able to choose which image you want to install over the network ??? 
Could all this be lying on the same server .- or should it be on each seperate subnets and servers ??? And does anyone have more information about this. 

I would really like to get this working instead of finding CD's, downloads a new - caurse people cannot put them back to their places! 

Thanks a lot 

P

---

### Post by niobos on 2007-11-08
I have never tried this myself, but technically I don't see any problem at all to get this to work.

I'd suggest the client boots a very small basic OS via PXE which asks you what to do: get either the linux or Windows disk image to restore it.

I have seen some enterprise-imaging software doing exactly that. (But, of course, I can't find the name in my empty brain). It was a linux based image-restore which allowed you to select any image from a file server. They had 4 different windowses (minimal, production, server, blabla)

---

### Post by Peque on 2007-11-09
Coool. 
See that sounds really interesting , if it's possible to choose between the images directly when booting ! 
Does anybody else have an idea about the name of that speticular software - caurse its sounds exactkly like the one I'm looking for

---

