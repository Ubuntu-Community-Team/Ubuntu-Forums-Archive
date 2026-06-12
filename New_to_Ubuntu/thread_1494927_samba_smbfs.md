---
title: "samba_smbfs"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by ck_linux on 2010-05-27
Hi,
I do have trouble to get a connection from my xubuntu pc to a windows share.
What every I tried it does not work (and never worked before).

1) I tried with: smb://ipaddress_server
   No error, no connection, just nothing

Next I tried with:
2) smbclient -L //192.168.1.1/data
   the answer was hopeful, I received an answer from the win-srv

   but I also get the error: session request to 192.168.1.1 failed (Called name not present)

3) Just login and see what will happen
   smbclient //192.168.1.1/data -U localadmin
   Enter localadmin's password:
   Domain=[W2000] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
   smb: \> dir
   NT_STATUS_ACCESS_DENIED listing \*

   smb: \>

That is it. I tried google, I tried chat.
As I understand I can connect via smbfs (or cifs) and because I user uid+pw+domain
I did not have to configure my xubuntu ws. Right ???

I also tried to mount a windows share, but below the surface they use smbclient
so as long as I did not solve problem 3) I can not get a connection.
I even removed the windows password, but the problem: NT_STATUS_ACCESS_DENIED remain.
If I connect with account: DUMMY + password BLA_BLA_BLA I received again the
NT_STATUS_ACCESS_DENIED error.

Checking on the windows machine I see there is 1 connection to the share (comming from ubuntu ws). 
Do I mis something,
do I have to configure / install anything.

Please help, or a link to help. Thanks

---

### Post by mikewhatever on 2010-05-27
I've been able to use samba with direct ip addresses: smb://192.168.2.123/, note the slash at the end. 192.168.1.1 is likely to be your router's gateway, is it not?

---

### Post by aust77 on 2010-05-27
I have a Windows share currently mounted on my Ubuntu PC, and this line of code has worked for me:

sudo mount -t FS_TYPE -O username=USERNAME //SHAREADDRESS/SHARE /mnt/MOUNTPOINT

If your share is passworded, you will then be prompted for the share password.

Hope it works for you as well as it's worked for me.

EDIT: Make sure you have the "smbfs" package installed (it's in the repositories)

---

### Post by ck_linux on 2010-05-29
new thought, stil no answer, stil no solution

So for everyone who did not have any problems I have a question.
1) is the workgroup name you use on windows the same as in ubuntu ?
2) did you use something others than: "WORKGROUP" as workgroup name??

Please let me know.

---

### Post by mapes12 on 2010-05-29
Have you tried pyNeighborhood as an alternative to Samba? It goes like this for me:-

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

### Post by ck_linux on 2010-06-06
Yes thanks for all input.
But ... that did not really help.

And finally I installed wireshark to see WHAT happens.
And it is Windows which created all the problems. 
- I added a USB fat formatted disk to the server, makes a share and **working**.
- Next I did a "easy share" (thanks to Peter) and again, **working**.

Now I have to find-out why windows is so extremely annoying and blocks the access
to the share where everybody does have access.

And   **IF**  anyone wants to leave a suggestion, please do !

To be continued.

---

