---
title: "how to run iso file"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by alexeyhurricane on 2009-04-20
i got a file to run it is called .iso and i can mount it but then i click install it doesnt work! what to do next? i dont know

---

### Post by cariboo on 2009-04-20
If you are running Windows, you need a program like [ImgBUrn]("http://www.imgburn.com/") to burn the iso to a cd, then you need to boot from the cd in order to try out or install Ubuntu.

Jim

---

### Post by RedSingularity on 2009-04-20
You could try Gmount if your using gnome.

---

### Post by lisati on 2009-04-20
An "ISO" file is to a CD a bit like what a photographic negative is to a printed photo: you can use it to make exact copies.

Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by alexeyhurricane on 2009-04-20
im using ubuntu and i mount it with archiver mounter but then i click install file as in instruction , but i think it should do like autorun or something !

---

### Post by alexeyhurricane on 2009-04-20
i dont want to burn it just open it and run it!

---

### Post by RedSingularity on 2009-04-20
Gmount is a good answer then.  Its very easy to virtually mount a CD.

---

### Post by alexeyhurricane on 2009-04-20
how do i get gmount then?

---

### Post by RedSingularity on 2009-04-20
sudo apt-get install gmountiso

---

### Post by alexeyhurricane on 2009-04-20
as i said i can mount but how do installation from then!

---

### Post by RedSingularity on 2009-04-20
Are you sure the CD is linux compatible?  I mean is it linux software?

---

### Post by antikristian on 2009-04-20
An iso is an "image" of a cd. To turn it into a real cd, follow this guide:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by alexeyhurricane on 2009-04-20
thank you everyone , it works now! big thanks.  gmount worked well!

God bless you!

---

### Post by Bölvaður on 2009-04-20
> **alexeyhurricane said:**
> im using ubuntu and i mount it with archiver mounter but then i click install file as in instruction , but i think it should do like autorun or something !

whow I had no idea about archiver mounter ^^.   for everyone that doesnt know what it is you can right click an iso and find it under "open with"

What is more interesting about it is that it doesnt work!

what I can do to mount the same iso is by running this in the terminal

sudo mount -o loop /home/bölvaður/Desktop/myDvD.ISO /home/bölvaður/Desktop/dvd/

note that the iso is on the desktop and I created a directory on the Desktop named dvd to mount the iso to.

I would belief using that program people are talking about would perhaps also work...


urrr... was too distracted... 8 min too late :(

---

