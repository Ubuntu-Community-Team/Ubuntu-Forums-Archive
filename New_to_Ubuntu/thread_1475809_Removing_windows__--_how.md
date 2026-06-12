---
title: "Removing windows  -- how?"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by cloyd on 2010-05-07
I am seriously considering removing windows from my dual boot netbook. I'm using UNR 9.10. The windows version is Vista. I'm using a GatewayLT3103u.

Other than thoroughly understanding the Gparted documentation, what else do I need to be aware of to avoid erasing the master boot record and taking care of GRUB (1.97 beta)?

Thanks in advance

---

### Post by sandyd on 2010-05-07
> **cloyd said:**
> I am seriously considering removing windows from my dual boot netbook. I'm using UNR 9.10. The windows version is Vista. I'm using a GatewayLT3103u.

Other than thoroughly understanding the Gparted documentation, what else do I need to be aware of to avoid erasing the master boot record and taking care of GRUB (1.97 beta)?

Thanks in advance
just delete the windows partition using Gparted, and expand the linux partition.

and you should be aware that you should back up your data before continueing, or you would become very sorry if GParted makes an error...:mad::mad:

---

### Post by cloyd on 2010-05-07
Thanks for the reply. I've been running a few errands . . . just got back. I thought that was about it, but  . . . will the grub menu self update, or what do I have to do there? 

and

 The reason I asked the original question was this: My windows partition is sda2. Disk manager says this one is bootable. My original Ubuntu partition is sda5. Disk manager does not list this one as bootable. My worry has been, what happens if I delete the bootable partition . . . or format it?

---

### Post by da burger on 2010-05-07
To update grub run ```
sudo update-grub
``` in the terminal.

---

### Post by The Cog on 2010-05-07
GRUB pays no attention to the bootable flag. It's not needed.

You may find that after deleting sda2, you will probably have to move the extended partition down before you can resize it. Then resize the sda5 within it. This will all take some time. Make sure you have a good backup first, in case of problems.

---

### Post by cloyd on 2010-05-07
thanks. That is the kind of unexpected thing that would get a noobie like me. I think the the task is set for tomorrow.  I appreciate the help.  I do happnen to have a 100 gig external hard drive lying around. It will do.

---

### Post by cloyd on 2010-05-08
OK. It is done. This little Gateway is free of Windows. It all works.  The only problem was this: I wanted to enlarge sda5, but I couldn't figure out how to move the extended partition down and so was not able to enlarge sda5.  I did run into a bit of trouble with permissions and had to change owner to me, and not root, on new partitions. 

How can I enlarge sda5?  I am wanting to make sure I have plenty of room for documents and applications. Would it be better or even possible to move home folder???

Thanks for the help.  Where else could an old Arkansan go and be helped by people in London, and Los Angles, and other unnamed places? It is nice. 

This is workable; I am going to wait just a while and see if anyone can tell me what I didn't understand that won't let me enlarge sda5.  However, even without that, it is almost time to mark the thread "solved." Thanks again.

---

### Post by cloyd on 2010-05-09
I considered this solved, but I figured out how to enlarge sda5. I didn't read documentation well enough earlier. Before I could enlarge sda5, I had to enlarge sda3, the extended partition container. So, I deleted sda2 (didn't need it). Then expanded sda3 to fill the empty space. Now there was room to expand an extended partition like sda5 within sda3. But when I clicked on sda5 in Gparted, the resize option was greyed out. Then I realized that the swap partition was mounted. There was no "unmount" option, but there was a "swapoff". Turned off swap, and all was ready to go.

I have no idea about any sda4. I've never seen it. It now shows up on my menus,  but if I click on it, I get the message, "does not exist." I didn't think so. 

Today, I used a live 10.4 usb to use Gparted. Yesterday I used 9.04.  The disk management tools give much more information in 10.4.

---

