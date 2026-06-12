---
title: "kernel_thread_helper+0x6/0x10"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by benjaminlee on 2010-12-07
Hi everyone.
 
I am a complete n00b when it comes to linux or programming in general. 
 
I had windows 7 installed on my laptop but decided to switch my OS to ubuntu. I tried both the netbook(10.10-netbook edition) and the desktop (10.10 -32bit version) version of ubuntu from [http://www.ubuntu.com/](http://www.ubuntu.com/) .
 
I am installing it on my Toshiba Satellite c650d laptop. I've read all the threads i can find that have kernel_thread_helper in them and this is how far i got:
 
Last night i was able to install ubuntu to my harddrive/booting from USB with the netbook edition. At the purple screen i pressed ESC, and then turned ACPI=off. It took a while to install ubuntu, but i was able to browse and download stuff. It said something like "changes wouldnt be made until i restarted my computer" i couldnt even find the restart button on ubuntu but i was able to browse the internet/download some applications. When i went to applications-->terminal it wouldnt pop up and there was nowhere to type.
 
I restarted my computer and ubuntu is no longer there... i just get the kernel_thread_helper+0x6/0x10
 
I did change the BIOS to boot from USB mediam but i dont know what is wrong...
 
i looked at this thread [http://ubuntuforums.org/showthread.php?p=10202543&highlight=kernel_thread_helper+0x6#post10202543](http://ubuntuforums.org/showthread.php?p=10202543&highlight=kernel_thread_helper+0x6#post10202543)
 
but have no idea how to pull up a terminal or anything like that... i can't go into applications because my operating system won't even work. I really wish i could talk to someone on the phone who can walk me through this.... I REALLY dont want to go back to windows.
 
I dont think it could be a hardware problem right? If i was using ubuntu yesterday?
 
someone please help me? It seems like a lot of people on this forum have the same problem as me.

---

### Post by benjaminlee on 2010-12-07
okay so here's where i am right now.
 
I formatted my USB stick so there's nothing else on it and re-installed the 10.10 netbook remix. 
 
1)I then plugged it into my laptop that i want to install ubuntu on.
2)I went to bios settings and booted from USB
3)I pressed ESC on the purple screen 
4) pressed F6, put an X beside ACPI=off
5) Installed it onto harddrive (note that when i try to load it from USB i get the kernel_thread_helper)
6)I now get the Install window and i click "erase and use the entire disk" instead of the "install alongside otherm operating system.
7) It is installing right now but i am fairly confident that it will let me use ubuntu... its just that when i restart will i have to change the BIOS to boot from harddrive?
 
I know i am going to run into problems again

---

### Post by Kortez999 on 2010-12-08
I have very similar problem, I'm not able to even load ubuntu from the live CD. I tried all the settings variants (like noapic nolapic, acpi=off, etc.) as advised in the installation instructions but, I always end up with the "[COLOR="Red"]**kernel_thread_helper**[/COLOR]" where it stops. The CD is fine, I just popped it into another computer and it worked OK.

---

### Post by petethepilot on 2011-01-07
I was running in to the same problem (a frozen install at kernel_thread_helper+0x6/0x10) and seem to have fixed it by using the alternate download found here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)
 
Hope that helps.

---

