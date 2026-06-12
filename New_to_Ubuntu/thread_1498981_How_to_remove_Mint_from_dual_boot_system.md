---
title: "How to remove Mint from dual boot system?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by germanix on 2010-06-01
I use Ubuntu Lucid but I also installed Mint as a dual boot to try it out. Mint works fine straight out of the box and I am sure a lot of people will be very happy with it but I still prefer the slick and clean Ubuntu desktop, the Ubuntu Menu and the window buttons on the left. So after testing Mint I came to the conclusion that Ubuntu was all I needed. I have a 80 GB hard drive and when I installed Mint in addition to Ubuntu I allowed Mint to take up half of the drive on its own partition. I would now like to remove the Mint installation again and make the full drive available to Ubuntu as it was before. I am not sure how to go about this and do not want to loose my settings in Ubuntu in the process if this can be avoided. I would really appreciate if someone could explain to me steps I need to take to accomplish this. I do not need to do this as a matter of urgency but I see no sense in keeping the Mint Distro on my drive when I know I will not be using it and anyway it takes up space.
I thank you all for your help in advance. Have a nice day all and any Mint users out there, please do not be upset, Mint is a great Distro just not my flavour.

---

### Post by Groodles on 2010-06-01
Which distro did you install second (ie which one wrote to the MBR last?)

---

### Post by TeoBigusGeekus on 2010-06-01
Install gparted if you don't have it already
sudo apt-get install gparted
Go to System->Administration->Gnome Partition Manager
Choose the Mint Partition and format it to the same format as your ubuntu partition.
Choose the ubuntu partition and resize it to its maximum possible size.
Done...
EDIT:
Don't forget to remove mint from your grub menu.

---

### Post by acrazyplayer on 2010-06-01
> **TeoBigusGeekus said:**
> Install gparted if you don't have it already
sudo apt-get install gparted
Go to System->Administration->Gnome Partition Manager
Choose the Mint Partition and format it to the same format as your ubuntu partition.
Choose the ubuntu partition and resize it to its maximum possible size.
Done...
EDIT:
Don't forget to remove mint from your grub menu.

you sadly cannot resize your ubuntu partition becuase you are using it. In order to resize it you must boot up a LiveCD and use gparted that way. There could be other ways Im sure but this would be the easiest for you.

Also you the best way to make sure ubuntu loads up fine after a reboot would be to do a "sudo dpkg-reconfigure grub-pc" and follow the instructions. Most everything will be the defualt.

---

### Post by TeoBigusGeekus on 2010-06-01
> **acrazyplayer said:**
> you sadly cannot resize your ubuntu partition becuase you are using it. In order to resize it you must boot up a LiveCD and use gparted that way. There could be other ways Im sure but this would be the easiest for you.

Also you the best way to make sure ubuntu loads up fine after a reboot would be to do a "sudo dpkg-reconfigure grub-pc" and follow the instructions. Most everything will be the defualt.
This^

---

### Post by germanix on 2010-06-01
> **Groodles said:**
> Which distro did you install second (ie which one wrote to the MBR last?)

Ubuntu was installed first.

Wow! thank you all for your quick response and good advice. If I understood correctly does this mean I should first do this:
Install gparted if you don't have it already
sudo apt-get install gparted
Go to System->Administration->Gnome Partition Manager
Choose the Mint Partition and format it to the same format as your ubuntu partition.
and then do this:
In order to resize the Ubuntu partition  you must boot up a LiveCD and use gparted that way. (can I assume that gparted is on the live CD?)
followed by:
make sure ubuntu loads up fine after a reboot typing the following in the terminal
 "sudo dpkg-reconfigure grub-pc"   and follow the instructions.

---

### Post by acrazyplayer on 2010-06-01
Very close, after deleting mint using gparted run the sudo dpkg-recon.... command to fix grub all up, then reboot to make sure ubuntu comes on for you. Then its safe to resize ubuntu from a LiveCD and yes gparted is part of the LiveCD, If not you could always install it, just wont be there next time you reboot lol, and then everything will be okay, you will have all your space back just for Ubuntu.

---

### Post by germanix on 2010-06-06
Thank you all for the great help. This worked as planned and I now have all the space back and running Ubuntu solo.
Have a nice day all.

---

