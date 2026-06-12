---
title: "No access to shares on Windows 2012 Server, Samba is installed."
date: 2018-12-23
forum: Networking &amp; Wireless
---

### Post by bert-jan54 on 2018-12-23
I am a Linux beginner and I’m currently looking for a good distro for my novice purposes. I’ve looked at Ubuntu, SuSe and elementary OS, among others, I’ve settled on Ubuntu for a couple of reasons but I’m stumped by a networking issue dealing with my old Windows server. My explanation is probably very n00b-like, but here goes..
 
 I’m running an old Window Server 2012 R2 Essentials machine, named BJSERVER, with a lot of movies, TV-series and such. I can access the shares on my Windows PC’ s without issues and also on Android devices and on a Macbook. But not on Ubuntu. The server is on a domain that I named BJ-NET. 

 - I’ve installed Samba. I can access a share that is on the Ubuntu machine on my Windows PC and use that without problems.
 - If I look in File Manager under ‘Other locations’  I do see my Windows PC, but not the server. There is however ‘Windows Network’. If I go there, There are two items; WORKGROUP and BJ-NET.
 - If I click on BJ-NET I get the following error:

'Unable to access location. Failed to retrieve share list form server: success'
 
 - If I type ‘smbtree’ in terminal I get the following listing:

WORKGROUP
   \\SHIELD               
   \\FRITZ-NAS            FRITZ!Box
      \\FRITZ-NAS\IPC$              IPC Service (FRITZ!Box)
      \\FRITZ-NAS\FRITZ.NAS         
   \\EPSONC2814B          
      \\EPSONC2814B\USBSTORAGE        EPSON
      \\EPSONC2814B\IPC$              IPC Service
   \\WIN-PC             Ryzen-PC
   \\ASUS-LAPTOP          Samba 4.8.4-Ubuntu
BJ-NET
   \\BJSERVER             Server

So it does list the server here. After reading some other post about this issue I added the line  '192.168.1.2   BJSERVER' to the hosts file. And I added the line 'name resolve order = host bcast lmhosts wins' to smb.conf. This had no effect.
I’m probably forgetting something obvious, but what amazes me is; in Elementary OS everything works out of the box. If I go to ‘Windows Network’  and click on ‘BJ-NET’ I have full access to the server.

All help is extremely appreciated

Bert-Jan

---

### Post by Morbius1 on 2018-12-24
Consider this a bump since I do not have an answer for you.

In fact I cannot explain how you are able to do this:
> If I look in File Manager under &#8216;Other locations&#8217;  I do see my Windows  PC, but not the server. There is however &#8216;Windows Network&#8217;. If I go  there, There are two items; WORKGROUP and BJ-NET."
What you should get when you click on "Windows Network" is an error message that states: [B]Folder is Empty

[/B]There's a reason for that and it has to do with a change samba made to the client side of things. It forces the maximum smb dialect to SMB3 and you can't have network discovery with SMB2/3. Only with SMB1 ( which samba calls NT1 ).

I just installed the current Elementary OS and the exact same thing happens ( actually the error message changes to **_This_ Folder is Empty** ) for the exact same reason so your symptoms are perplexing.

*On my network which has Win10 on it I can force the Linux system back to the old way by forcing "client max protocol = NT1" in smb.conf and rebooting. Now when I open up Nautilus I will see the WIn10 server but I will not be able to connect to it or even get a list of shares because Win10 disabled SMB1 on the server side so access is impossible.*

About the only thing that does match your description is smbtree. It will list the server but you will notice it will not enumerate the shares on that server. Same thing happens to me. If I run smbclient ( smbclient -L win10 ) I can get a list of shares but it will let me know that access is not possible because of the smb1 issue.:
> protocol negotiation failed: NT_STATUS_CONNECTION_RESET

---

### Post by bert-jan54 on 2018-12-26
I posted the same issue on the Dutch Ubuntu forum (as I'm from Enschede, The Netherlands) and got some tips to add:

[B]client min protocol = SMB2_02
client max protocol = SMB3[/B]

to **[global]** in smb.conf. When I did that I got exactly what you are describing; a 'Folder is Empty' message. 
However, I did find a solution. After installing cfis-utils (I'm really new to this, I should have done that earlier, but only found out about this after looking through a lot of posts) I was able to at least mount the shares with 

[B]sudo mount -t cifs -o username=username,password=password //BJSERVER/Photos /mnt/Photos

[/B]A user on the Dutch forum then suggested I try adding **smb://BJSERVER/Photos** to 'Other locations' - 'Connect to server'. That also worked. So I bookmarked the shares there and now have access.

Thanks for your help!

Bert-Jan

---

