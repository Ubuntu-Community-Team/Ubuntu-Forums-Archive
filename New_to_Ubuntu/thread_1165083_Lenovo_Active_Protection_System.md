---
title: "Lenovo Active Protection System"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-05-20
Hi,

I know that there has been some discussion about this, but a lot of it seems to be out-dated. I own a Lenovo X200 Tablet. All Lenovo computers have an excellent feature called the Active Protection System that detects laptop acceleration and protects the hard disk from fall, shock, etc. 

Can someone please tell me how to get this working? In Ubuntu 9.04 do i still have to re-compile the kernel, or can i just download the package off synaptic?

Thanks

---

### Post by Didius Falco on 2009-05-20
I did a little googling on the subject, as I don't use a Lenovo, but I did find the following. Have a read through this bug report - it appears to be do-able in Jaunty:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311336)

I hope this helps...

Regards,

Didius

---

### Post by akimatsu123 on 2009-05-20
> **Didius Falco said:**
> I did a little googling on the subject, as I don't use a Lenovo, but I did find the following. Have a read through this bug report - it appears to be do-able in Jaunty:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311336)

I hope this helps...

Regards,

Didius

Thank you very much. I used one of the links in the replies ([http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_Thinkpad_T400#Active_Protection_System]("http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_Thinkpad_T400#Active_Protection_System")) to set up my hdaps. 

now when i shake my computer i do get a response from hdaps. however, the instruction says i can run "hdaps-gl" in the terminal to see the position of my computer. i run that, and the sensor readings seem to be messed up. when i tilt the computer up, it shows as it being tilted sideways, and when i tilt the computer sideways, it shows it as being tilted up. will this actually mess up the performance of the active protection system? personally i don't care if my computer thinks my computer is being tilted upwards when its not, but if it affects hdaps then i want to fix it. 

thanks

---

### Post by Didius Falco on 2009-05-20
> **akimatsu123 said:**
> Thank you very much. I used one of the links in the replies ([http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_Thinkpad_T400#Active_Protection_System](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_Thinkpad_T400#Active_Protection_System)) to set up my hdaps. 

now when i shake my computer i do get a response from hdaps. however, the instruction says i can run "hdaps-gl" in the terminal to see the position of my computer. i run that, and the sensor readings seem to be messed up. when i tilt the computer up, it shows as it being tilted sideways, and when i tilt the computer sideways, it shows it as being tilted up. will this actually mess up the performance of the active protection system? personally i don't care if my computer thinks my computer is being tilted upwards when its not, but if it affects hdaps then i want to fix it. 

thanks

You are very welcome! 

I don't use a Lenovo, so I can't really give you any answers on that. I did notice in the link in your post that it said:

 >  You can change the sensitivity value and other things in this file: "**/etc/default/hdapsd**".


You might want to have a look in that file and see if there are any settings that apply. Otherwise, your best bet would be to email the person that wrote that guide. His address is at the bottom of that guide.

You might also find some help at this forum, though on the first page I did see that someone had recently asked the same question and hadn't gotten a response as yet.

[http://forum.thinkpads.com/viewforum.php?f=9&sid=0601397665aae4160e5757ba33bd3131](http://forum.thinkpads.com/viewforum.php?f=9&sid=0601397665aae4160e5757ba33bd3131)

I'd also recommend reading the man page and/or any documentation that came with hdaps-gl.

Regards,

Didius

---

