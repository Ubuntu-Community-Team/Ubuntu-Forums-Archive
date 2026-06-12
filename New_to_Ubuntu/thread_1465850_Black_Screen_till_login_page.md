---
title: "Black Screen till login page"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by hyperzahranism on 2010-04-29
Hi everyone 

1st congratulations to all ubunteros the new LTS Lucid Lynx 
I love the new theme and the facinating colors in it 

But I have some problems I would really appreciate your help please
By the way I'm using eee Asus netbook, Lucid Lynx 10.04 desktop version
I installed ubuntu through startup USB 

**_1st: No startup demo till login page_**

when I start my netbook I see a blank black page till the login page shows up, I don't see the ubuntu startup processing page which I see it only when I shut down my computer


**_2nd Thing, No icons on system at the top panel _**

[ATTACH]154726[/ATTACH]

it was easier on 9.10 to fix this problem by configuring the appearance and the layout directory and allowing icons 

but Now with the new ubuntu appearance there is no layout directory to solve this problem 



The 3rd problem: 

[ATTACH]154725[/ATTACH]

I don't know how to make this closer to the upper panel 



Thanks for the great help and I really appreciate your great work around here 

Best Regards

---

### Post by madjr on 2010-04-29
1) blackscreen happens sometimes, no big deal is plymouth

2)
[http://www.omgubuntu.co.uk/2010/04/easily-access-missing-interface-tab.html](http://www.omgubuntu.co.uk/2010/04/easily-access-missing-interface-tab.html)

hmm i like the purple screenies :)

---

### Post by hyperzahranism on 2010-04-30
Thank you so much madjr for having the time to look around my thread 
I really appreciate your effort and I'm a big fan of OMGubuntu but I didn't noticed that article before, it's really helped showing the missing icons 

But I still looking for a help to solve the 1st & 3rd problem 

Thanks again for the great ubuntu support team and users

---

### Post by cespinal on 2010-04-30
+1 subscribing to this :P I want my bootsplash back!!!! :)

---

### Post by raamee on 2010-04-30
Yea, me too having this blank screen problem? How to solve this?

---

### Post by cespinal on 2010-05-01
Found a solution for this: 

Open a terminal and type the following:

# to become superuser (root) (for whatever reason I could not use just sudo echo ... ):
sudo su
# type your password here, then:
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
# exit root-mode:
exit

source: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

---

### Post by hyperzahranism on 2010-05-01
> **cespinal said:**
> Found a solution for this: 

Open a terminal and type the following:

# to become superuser (root) (for whatever reason I could not use just sudo echo ... ):
sudo su
# type your password here, then:
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
# exit root-mode:
exit

source: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

Thank you so much **cespinal**
Now I have my bootsplash Back 

Thanks again 


I'm almost there, I still have one problem here 
how to make the notification cloud closer to the top panel

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154725[/IMG]


Thank you guys for your help

---

