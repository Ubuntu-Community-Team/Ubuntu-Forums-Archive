---
title: "stuck whilst installing BURG"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Dr. div11 on 2011-05-14
hi i am trying to install burg but heres  the problem.. i get the first and the second step right..eg

1)
sudo add-apt-repository ppa:bean123ch/burg


correct


2)
sudo apt-get update && sudo apt-get install burg burg-themes


 i get this correct also


NOW HERES THE PROBLEm


[INDENT]sudo burg-install “(hd0)”


after i apply this command.. it comes as ..
cannot stat hd0


.. what do i do..
i deperately wanna install burg..


where ami going wrong..???

[/INDENT]

---

### Post by wildmanne39 on 2011-05-14
> **Dr. div11 said:**
> hi i am trying to install burg but heres  the problem.. i get the first and the second step right..eg

1)
sudo add-apt-repository ppa:bean123ch/burg


correct


2)
sudo apt-get update && sudo apt-get install burg burg-themes


 i get this correct also


NOW HERES THE PROBLEm


[INDENT]sudo burg-install “(hd0)”


after i apply this command.. it comes as ..
cannot stat hd0


.. what do i do..
i deperately wanna install burg..


where ami going wrong..???

[/INDENT]
HI, I have not tried to install that program but the drive is usually refered to as sda or sdb something like that.

---

### Post by wildmanne39 on 2011-05-14
> **Dr. div11 said:**
> hi i am trying to install burg but heres  the problem.. i get the first and the second step right..eg

1)
sudo add-apt-repository ppa:bean123ch/burg


correct


2)
sudo apt-get update && sudo apt-get install burg burg-themes


 i get this correct also


NOW HERES THE PROBLEm


[INDENT]sudo burg-install “(hd0)”


after i apply this command.. it comes as ..
cannot stat hd0


.. what do i do..
i deperately wanna install burg..


where ami going wrong..???

[/INDENT]

Hi, I looked in synaptic package manager and it has an mlburg that is for scripting, if that is what you are looking for just use synaptic to install.:D

---

### Post by hal8000 on 2011-05-15
Hi your repository failed to load for me, so I did a search and found one that worked.
Here is how I got Burg Installed on Natty 11.04


sudo add-apt-repository ppa:n-muench/burg 
sudo apt-get update 
sudo apt-get install burg burg-themes


At the last step burg was configured in the command line, a couple of questions that you just need to OK, (its not mouse driven just tab, space, enter to navigate). The final install was to select hard drive. As I have 2 hard drives, sda and sdb it was only a matter of telling Burg which drive to install the mbr to and that is my current drive. If you have more than one drive and are unsure, type "df" in the terminal. The drive with the mounted "/" filesystem is the one youre using.

There was no need to run the last step
sudo burg-install

Here's another page of info:
[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1679-how-to-install-burg-in-ubuntu-](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1679-how-to-install-burg-in-ubuntu-)

Hope that helps, if it gets you working just append [solved] to your first post title.
One other point, in my case I have multiple OS across two drives and Grub 2 makes multiple entries and some entries that don't work on my system.
Burg uses the same config files for grub two but adds graphics and icons and has much more eye candy than grub2.
Hope that helps.

---

### Post by mcduck on 2011-05-15
> **Dr. div11 said:**
> 

NOW HERES THE PROBLEm


[INDENT]sudo burg-install &#8220;(hd0)&#8221;


after i apply this command.. it comes as ..
cannot stat hd0


Your problem is the quotes, the site where you are reading the instructions probably uses smart quotes, while command-line requires simple straight quotes instead.

```
sudo burg-install "(hd0)"
```

---

### Post by Avidanborisov on 2011-05-15
you can install via synaptic with GUI which is much easier, follow this guide:
[http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/](http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/)
or try this command:
```
sudo burg-install /dev/sda
```

---

