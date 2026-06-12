---
title: "Network Connection with Windows Vista"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by yangt299 on 2009-04-27
Hi,

I've been using Ubuntu for about 1/2 a year now, and all this time my Ubuntu computer has been unable to recognize my Vista computer, and vise versa. Ultimately, my goal is to share one of my Ubuntu folders with Vista, and I found an article online on how to do this, but to do this my computers must be able to recognize each other on the network. Why don't my computers recognize each other? Please help! Again, my goal is to share a folder between the two computers. I don't know if there are any ways to approach this that do not require a network connection, but if there is, please offer the alternative! Thanks a lot!

---

### Post by lisati on 2009-04-27
Have a read [here]("http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting") for information about file sharing between Windows and Ubuntu. Some of the instructions are based around XP, feel free to ask questions if you get stuck with Vista.

---

### Post by yangt299 on 2009-04-27
Thanks, could anyone give me a bit more information on Samba? I need for my Ubuntu computer to recognize my Vista computer in the network, and vise versa. Will Samba help me achieve this? 

Thanks again!

---

### Post by yangt299 on 2009-04-27
Additionally, when [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting) mentions "path" under [MyFiles], can you change this path to whatever folder you wish to share with your Windows computer? Thanks so much, and sorry if I'm asking too many questions.

---

### Post by doas777 on 2009-04-27
I usually add these line to my clients smb.conf:
```
client NTLMv2 auth = yes

```
so that samba can use the default authentication protocol in vista.
be sure to edit the file with sudo/gksu and reload samba after doing so.

good luck

---

### Post by MysticGold04 on 2009-04-27
Yes, that should work. I would recommend that you create a new folder to be shared with Windows and then copy whatever files you want into it instead of using your own home folder for instance... Samba works well, I am using it to share files and a printer to Windows clients.

---

### Post by yangt299 on 2009-04-27
Thanks guys. I'm currently modifying my Vista computer using the instructions from [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting). I'm having problems with these instructions, which are reproduced below: 

> 2. Changing network settings in Windows

Now we should let Windows know that there's a WINS server active in the network.

If you had to change "wins support" to "no" above skip this step!

- Click "START"
- Click "Control Panel"
- Click "Network Connections"
- Find your "LAN Connection"
- Right-click the icon and select "Properties"
- Select the "TCP/IP" Protocol and click the "Properties" button
- Click "Advanced"
- Select the third Tab entitled "WINS"
- Click "Add"
- Type in the ip-address of your Linux box
- Click "Add"
- Select "Use NetBIOS over TCP/IP"
- Click "OK"
- Click "OK"
- Click "OK"
- Reboot Windows

Upon reboot you may now map the network drive within Windows.

With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
NOTE: Adjust this to the hostname and sharename you chose above!
- Click "Finish"

With WINS disabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\<ip-address>\MyFiles
NOTE: To find out the ip-address of your Linux box type "ifconfig" inside a terminal and find the ip for the correct interface (i.e. eth0). Don't forget to adjust the sharename to the name you chose above.
- Click "Finish"

That's it - samba is up and running now

It seems as if Windows XP's format of the Network Settings is different than Vista's. Does anyone know how to achieve the same results using Vista? Thanks again!

---

### Post by stchman on 2009-04-27
> **yangt299 said:**
> Hi,

I've been using Ubuntu for about 1/2 a year now, and all this time my Ubuntu computer has been unable to recognize my Vista computer, and vise versa. Ultimately, my goal is to share one of my Ubuntu folders with Vista, and I found an article online on how to do this, but to do this my computers must be able to recognize each other on the network. Why don't my computers recognize each other? Please help! Again, my goal is to share a folder between the two computers. I don't know if there are any ways to approach this that do not require a network connection, but if there is, please offer the alternative! Thanks a lot!

It has been my experience that XP/Vista shares are at best spotty for a Linux box to connect to.

I believe the original intent for Samba was for Windows machines to connect to Linux machines, not the other way around.

I personally use NFS for my home network as I have all Linux machines.

---

### Post by yangt299 on 2009-04-27
So basically, what I believe you are saying is that Samba will not work for my purposes. 

If my beliefs are correct, then does anyone know a solution to my problem? My biggest problem is that neither of my computers recognize each other in the Network. Does anyone know why, and can anyone help me fix this? Thanks!

---

### Post by stchman on 2009-04-27
> **yangt299 said:**
> So basically, what I believe you are saying is that Samba will not work for my purposes. 

If my beliefs are correct, then does anyone know a solution to my problem? My biggest problem is that neither of my computers recognize each other in the Network. Does anyone know why, and can anyone help me fix this? Thanks!

I have never had any luck with Linux connecting to an SMB Windows share.

Some of the other forum members might be of more help than I since I have been Windows free for quite some time.

---

### Post by yangt299 on 2009-04-27
OK, thanks. Has any of you Ubuntu users here successfully connected your Ubuntu computer to a Vista? How did you do this? Thanks!

---

### Post by yangt299 on 2009-04-27
Any help please?

---

### Post by doas777 on 2009-04-27
did you enable ntlmv2 in your smb.conf?

---

### Post by Bradtek on 2009-04-27
Can the computers see each other ?
if no
Do they both have the same Workgroup ?

What errors (if any) do you get ?

I have no probs sharing Ubuntu & XP, 
I can't see how Vista would be much different 
other than having different interface for the settings.

---

### Post by Miljet on 2009-04-27
I remember that XP used a default workgroup name (I believe it was MSHOME). When Vista came out, it was set to a different default. It's been too long for me to remember what it was. That caused many people, myself included, a lot of grief trying to get their computers to see each other over a network.

The bottom line is that you can share files with Vista. But like most others here, I haven't used Vista for quite a while now and therefore can't give you step-by-step instructions.

---

### Post by yangt299 on 2009-04-27
> did you enable ntlmv2 in your smb.conf?

Where can I find smb.conf?

> Can the computers see each other ?

Yes they can. However, I can access my Vista from Ubuntu, but when I try to access Ubuntu from Vista, there is an error message that is displayed. They are both in the same workgroup. The error message is something like "cannot find (computer name). Click here for more details." and when I click "here" the error message displays "does not recognize computer" or something like that. Any help?

---

### Post by doas777 on 2009-04-27
> **yangt299 said:**
> Where can I find smb.conf?


you can edit your smb.conf by opening a terminal and pasting in:
```
gksu gedit /etc/samba/smb.conf
```add the line in my previous post, save, close and then run:
```
sudo /etc/init.d/samba restart
```hopefully that will do it.

---

### Post by yangt299 on 2009-04-28
Yes, it is enabled. 

> hopefully that will do it

what is "it"? 

will simply having this enabled allow my computers to share folders with each other?

Thanks again!

---

### Post by yangt299 on 2009-04-28
any help?

---

### Post by doas777 on 2009-04-28
ok, NTLM is an authentication protocol for windows networks, and is used to encrypt passwords and other sensitive info when establishing a connection with a windows/samba share. Samba by default uses lm and ntlm, but vista uses ntlmv2, so samba needs to be configured to talk that langague. you should now be able to access a share and login to it.

---

