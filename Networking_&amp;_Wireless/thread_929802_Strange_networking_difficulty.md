---
title: "Strange networking difficulty"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2008-09-25
In my limited previous limited experience with Ubuntu networking, each computer found the other all by itself. Beginners luck!

I can ping each of two Unbuntu computers from the other, but clicking on Places/Network on each does not reveal the other. Computer A (7.04) sees itself, my windows computer, and my wife's windows computer, but not B (my new Ubuntu 8.04 computer)

Does B also need NFS in order to find the others and for the others to find it?

BTW, where is "Shared Folders" in 8.04? I can find Network and Network Tools, but not Shared Folders.

---

### Post by NullHead on 2008-09-25
> **Odyssey1942 said:**
> In my limited previous limited experience with Ubuntu networking, each computer found the other all by itself. Beginners luck!

I can ping each of two Unbuntu computers from the other, but clicking on Places/Network on each does not reveal the other. Computer A (7.04) sees itself, my windows computer, and my wife's windows computer, but not B (my new Ubuntu 8.04 computer)

Does B also need NFS in order to find the others and for the others to find it?

BTW, where is "Shared Folders" in 8.04? I can find Network and Network Tools, but not Shared Folders.

You're going to want to click on "share folder" and when it asks you, install samba instead of NFS. Samba is the windows networking protocol and NFS is for linux.

When you browse a folder in your homedirectory, right click on it and there will be share folder in that list.

---

### Post by Odyssey1942 on 2008-09-25
Nullhead, Thanks for yours, but "BTW, where is "Shared Folders" in 8.04? I can find Network and Network Tools, but not Shared Folders."

---

### Post by superprash2003 on 2008-09-25
as mentioned above,, you would need to install samba.. and the share folder option is available when you right click on the folder you want to share..for this you first got to install samba..
guide : [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by Odyssey1942 on 2008-09-25
Prash, Thanks for yours. I have already installed NFS on the 8.04 computer, but it still doesn't see the 7.04. Does the computer need restarting?

I thought installing NFS also installed SAMBA in the process. I have no memory of installing SAMBA on the 7.04 machine. Do I need to install SAMBA separately?

Also the 7.04 machine is set up for DCHP. I assume that the 8.04 machine should be as well?

Also installing NFS did not create Shared Folders.

Edit: I checked and SAMBA is indeed installed. Looking at your last post, the folder (actually /home which is a separate partition) that I want to share is on the 7.04 computer. It is already set up to share and my objective is to copy it over to the 8.04 computer because the 7.04 one is being moved to another location.

---

### Post by Odyssey1942 on 2008-09-25
Perhaps someone else has some ideas on this? Sorry for the push, but I am trying to take the 7.04 computer to another city in an hour or so. Thanks.

---

### Post by NullHead on 2008-09-25
You'll need to install samba as well as NFS. You can install samba with *"sudo apt-get install samba"* and then navigating into a folder, right clicking on the folder and selecting "share folder" or something to that effect. There you can change settings as to which will effect what kinds of computers can access it.

---

### Post by Iowan on 2008-09-25
The Samba-client comes pre-installed (you should be able to view shares on other machines). Samba-server must be installed separately.  Some threads suggest SMBFS must also be installed.

---

### Post by Odyssey1942 on 2008-09-29
Nullhead and Iowan,

thanks for yours which came in after I had to leave. Back to the problem. To refresh, my 7.04 machine works perfectly and contains the folder (actually  /home ) that I want to copy to the new machine (8.04). /home appears to be shared.

the problem is that neither computer can see the other, although they can ping each other and each can see the two Windows computers on the lan.

I don't recall installing Samba-server on the 7.04 and am sure that I did not on the 8.04. Does it need to be installed on both, or just one and if one, which?

TIA

---

### Post by NullHead on 2008-09-30
Well you can try opening your file browser to your home directory and typing in ```
**smb://**ipaddress_of_the_machine_you_want_to_connect_to
```into the address bar. That's what I have to do sometimes, but it doesn't always work. You also might have to put the name of the shared folder after the ipaddress.

Here is an example of how I use that: ```
smb://192.168.2.20/public
```I just pop that into the addressbar or my file browser, and it brings up my shared folder that my server is sharing, public.

---

### Post by Odyssey1942 on 2008-09-30
NH, I can ping the other computer successfully and I put:

smb://192.168.0.108   into my Firefox browser and get a 

small white box at the top of the screen which contains two lines:

"index of smb://192.168.0.108/   (on the top line) and

NAME      SIZE        LAST MODIFIED"  (on the second line)

This is encouraging but not very rewarding.


and I also put 

smb://192.168.0.108/home into my Firefox browser and get a 

File Not Found message

Is "  smb://192.168.0.108/home  " exactly correct syntax because I know how unforgiving linux is with one character incorrect?

---

### Post by NullHead on 2008-09-30
You want to put that into your file browser, or nautilus. Just open the Places menu and click on your home directory, that will bring up a filebrowser which is called nautilus. *Then* you'll want to put smb://address into *nautilus's* address bar ;)

---

### Post by Odyssey1942 on 2008-10-01
NH,

Using Nautilus (from the 8.04 computer) with:

smb://192.168.0.108/ (ip address of the 7.04 computer)

there is no error message and it shows a folder named print$. Clicking on the print$ folder brings up a sign-in box with the lines

Enter Password
Password required for share print$ on 192.168.0.108
Username: Robert
Workgroup: Workgroup

While the name Workgroup originates from my Windoze computers on the lan, the second line above seems clear that it is looking to the 7.04 computer. Yes? (The 7.04 computer prints through an XP computer which has the printer attached and I assume the 7.04 just picked up the name from the windows network name.)

Now if I enter:

smb://192.168.0.108/home/

or

smb://192.168.0.108/home/robert/

I get the error message:

Couldn't display "smb://192.168.0.108/home/' or smb://192.168.0.108/home/robert"
Error: Failed to mount Windows Share

in the 7.04 computer, I think I have properly shared the folder /robert under /home, i.e., /home/robert

and when viewed with Nautilus, there is a little red circle with what appears to be a white icon of a house on /robert, which I take to mean that it is a "home" folder. If I right click on /robert and chose Share Folder, it brings up a box entitled Settings for folder '/home/robert' with this info:

Shared Folder
Path: /home/robert
Shared Through: Unix networks (NFS)
Hosts
Allowed host/network | Read only
192.168.0.106

(BTW, how does one capture a screen to post into a thread so that you can see exactly what I see?)

Also I don't see any info on the share name I gave it (if I did, i.e., have no recollection of actually doing that and cannot see how to do it) and suspect that I need to figure that out so that I can enter the correct share name in the Nautilus on the 8.04 computer, without which it is not likely to connect.

So from the above, unsure whether this is a naming issue or a mounting issue?

Right clicking on /robert and choosing Properties and looking at the Basic tab, the line

Name: robert

so "robert" presumably just reflects the folder name.

I am still confused about the 8.04 computer because there is still no "Shared Folders" in System/Admin and if I right click on /robert in that computer there is no Share Folder there either. Clearly I need to install something on that computer. Have installed NFS, which installed the Samba Client. What else is needed? Should I add: system-config-samba?

Many thanks for your additional guidance.

---

### Post by NullHead on 2008-10-01
Sure, you can use system-conf-samba or what ever you called it ;) I have no experience with it, but I'm sure you could probably figure something out. 

I'm curious about something .. perhaps I'm a bit too inexperienced with these things, but perhaps you could try this for me and let me know if it works. 

Try adding the share manually into your samba config. Do that like so: ```
gksudo gedit /etc/samba/smb.conf
```
Put in a block like this at the very bottom: ```

[Home]
      comment = this is my home directory
      path = /home/username
```
Restart samba, ```
sudo /etc/init.d/samba restart
``` Then use try to access your other computer like I said earlier.

---

### Post by Odyssey1942 on 2008-10-01
Just want to make sure that I understand your suggestion. On the older computer that I want to reach (in order to copy /home/robert to the newer computer), the folder is shared already.

On the newer computer, there is nothing there to share. I am only interested in being able to when the need arises.

So on which computer should I modify the Samba config file and what will this accomplish? Hope I'm not being dense here.

---

### Post by NullHead on 2008-10-01
Oh my, you're not dense at all! you're trying to understand my vague instructions that I wrote in a hurry :lolflag:

Ok, so from what I understand, you're trying to copy /home/robert from the 7.04 machine over to the 8.04 one? My instructions were intended to manually share the /home/robert folder on the 7.04 computer so you can use smb://192.168.0.108/home to get to your home folder from the other 8.04 machine to copy the content. 

That's what I was hoping would happen, but I'm not 100% on this. It won't cause any harm, but it'll either work or it won't work.

---

### Post by Odyssey1942 on 2008-10-01
You do understand my objective, and the folder that I want to copy over is shared.

But until the new machine can see the old one, I can't copy the folder.

Any ideas on how to solve the networking issue?

---

### Post by cariboo on 2008-10-01
Ubuntu has been trying to make networking easier with samba, but so far in my opinion they have messed it up pretty good. I have been trying to find documentation on what they are doing but so far all I get is unfinished documents. If you want to copy from the home directory on your old coputer to your new computer, you would probably be just as well off setting up NFS,it is a lot less aggravation. Here is a link to a howto.

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Jim

---

### Post by Odyssey1942 on 2008-10-02
Hello Jim,

Thanks for this which I am still studying.

As you can tell from my questions, I am still at beginner level in linux. Can these packages all be installed with Synaptic without further tweaking? For example, I had already installed NFS client using Synaptic.

---

### Post by Odyssey1942 on 2008-10-02
I had no idea how close the (partial) solution was. I selected "Windows Network" in folder sharing on the older computer and presto, there was my old computer's /desktop visible on my new machine.

However, even though I marked it as available as Read Only, Read and Write, and every thing in between, I cannot copy it from the old to the new. The error message is:

The folder cannot be handled because you do not have permission to read it. Will be experimenting to get past this, but if you can see the solution, I would be grateful for your early advice as I would like to take this computer with me to another city today.

---

### Post by Odyssey1942 on 2008-10-02
Right there indeed. Right at the bottom of the permissions screen is the line:

Apply permissions to enclosed files.

Now copying.

Many thanks for your continuing assistance.

---

### Post by NullHead on 2008-10-02
So it works now?

---

