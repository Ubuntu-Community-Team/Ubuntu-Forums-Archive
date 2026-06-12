---
title: "How do I: Ghost an image?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by TechDragon on 2010-02-11
I am trying to create a useable system rescue drive.  Currently we utilize ghost and have *.gho images.  Ghost will run inside of linux using wine but fails to see the available hard drive although Ubuntu does see it.  Is there anything available for linux that will create *.gho and use *.gho files.  Opensource is wonderful but a commercial option is also acceptable.

Please and thank you

---

### Post by Grenage on 2010-02-11
I am not sure of the format, but Clonezilla is an excellent option.  You can use 'dd', but for most people CloneZilla is much better.

---

### Post by bumanie on 2010-02-11
I prefer dd, but [here]("http://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software") are some alternatives. As you can see, there are many that will do ext3 (and I assume ext4 - but you had best check the latest pages for a tool you choose, just to make sure). [Here]("http://en.wikipedia.org/wiki/Dd_%28Unix%29") is a page for dd if you like.

---

### Post by TechDragon on 2010-02-11
ok, that comparision list states that ghost will work maybe my ghost is to old.

It has to utilize the .gho extension which is a ghost proprietary extension.  I just didn't know if another program could utilize it like openoffice use .doc, .xml etc

---

### Post by Mark Phelps on 2010-02-11
> **TechDragon said:**
>  ... It has to utilize the .gho extension which is a ghost proprietary extension...

That's going to be the limiter.

I've used Clonezilla, Remastersys, and PING in the past -- and NONE of those could use a .gho file.  Maybe the most current versions can, but I would seriously doubt it.

---

