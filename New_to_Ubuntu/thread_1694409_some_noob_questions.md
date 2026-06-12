---
title: "some noob questions"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by edgeit on 2011-02-24
First time I popped in ubuntu installer I got a menu list that allowed me to scan memory / hard disk / cd as well as the selection for installation. Now everytime I boot to disk it shoots straight to the installer. My reason for asking is I would like to run the memory test and see how it compares to [http://www.kelleycomputing.net/rember/]("http://www.kelleycomputing.net/rember/") & [http://www.memtest.org/]("http://www.memtest.org/") (anyone familiar with those utilities 

Lastly if I am partitioning an external drive to have this installation on one partition what is the best size for ubuntu to run efficiently. I will not be doing anything more then putzing around on it, learning the basics, so I stress I am no power user.

Forgetting last question will update post later.

---

### Post by edgeit on 2011-02-24
found some info on FAQs reading up now.

---

### Post by Paqman on 2011-02-24
> **edgeit said:**
> I would like to run the memory test and see how it compares to [http://www.kelleycomputing.net/rember/]("http://www.kelleycomputing.net/rember/") & [http://www.memtest.org/]("http://www.memtest.org/") (anyone familiar with those utilities 


The memory test that runs from the bootloader is memtest86, just like the one you link to above.

> 
Lastly if I am partitioning an external drive to have this installation on one partition what is the best size for ubuntu to run efficiently.

You will need to create a root partition that's at least about 6GB in size, 10GB or 20GB would be better. You'll also need to create a swap partition, but all this can be done by the Ubuntu installer, so you don't need to have it prepared beforehand.

---

### Post by edgeit on 2011-02-24
Is there something I need to do following the install that allows my mac to recognize the installation is on a partitioned external hard drive, connected through fw800. 

I formatted my drive to ext4, assigned the swap drive, and specified the mount point to  " / "

my boot list doesnt show the ext4 partition. just my built in apple one.

---

### Post by Paqman on 2011-02-24
You might find your question is better directed at our [Mac forum]("http://ubuntuforums.org/forumdisplay.php?f=328"). That's where the folks with experience putting Ubuntu on Macs will be.

---

### Post by deconstrained on 2011-02-24
> **edgeit said:**
> found some info on FAQs reading up now.

THANK YOU.

So many people (myself sometimes included) fail to do this.

---

