---
title: "Thumb Drive Permission Issues"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by killjoy123987 on 2009-05-18
I've been using linux for about a half a year now and i just upgraded to 9.04 32-bit edition and now none of my external devices will mount due to permeissions.

Whenever I try to mount one of my external devices an error message comes up saying: "Cannot mount volume. You are not privileged to mount the volume." In order to mount it I now have to go into the terminal and mount it as root.

I've tried chmod, chown and but it will still give me the same message.
when I use ls -l i get:
brwxrwxrwx 1 jeremy disk 8, 17 2009-05-18 16:17 /dev/sdb1

any help would be appreciated thx

---

### Post by Terry of Astoria on 2009-05-18
After I upgraded to 8.04 I had similar issues and discovered that they had something to do with my previously-customized /etc/fstab file.
   I think I actually removed some entries and that fixed the problem for me. 
Remember to back-up your fstab or any other configuration file before changing it.

---

### Post by qjmoss on 2009-05-18
Now, this is a little foggy for me.

But I also had this problem.

And I _think_ the way I solved this was to go under System->Adim.->Authorizations.

Now, this is going to make me sound a little, non-legit.

But when you open authorizations, look for something that says external drive, and grant it authorizations.


If I find a usb drive, or external that I can plug in and see it for myself I will repost, but i hope this little bit of information will help you a little.

If anyone has a better answer, take it, because Im just pulling this out of the back of my mind

):P

---

### Post by killjoy123987 on 2009-05-18
@qjmos: I tried what you said, there was an entry for mounting and unmounting external drives and I gave myself authorization but unfortuantly I still cant mount anything. 

@Terry: I opened the /etc/fstab file but there isn't an entry in there for /dev/sdb1 so im not sure if i have to edit that file

thx for the help I appreciate it :)

Edit: I restarted my computer and re-opened the /etc/fstab file and I found the /dev/sdb1 file, I deleted that entry and now I can mount my external drives again :D. thx again for your help

---

### Post by Terry of Astoria on 2009-05-18
I had some different issues when I upgraded to 9.04 and I reverted back to 8.10. I found it really was easy to save my data and then reinstall, but if you have a ton of data or customization on your machine it can be a pain. To experiment before I switched back, I ran Ubuntu off my thumb drive for a while. It was really easy and it worked just as well as from the HD. Just use the iso from 8.10 to make a bootable thumb drive from the System menu. Then set up yur system to boot from that USB device, and  . . . Just a thought. . . . .

---

