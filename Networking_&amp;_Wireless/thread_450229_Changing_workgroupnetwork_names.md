---
title: "Changing workgroup/network names"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by the lemming on 2007-05-21
I have a slight problem and I don't know how to resolve it.  I have a laptop and PC on a wireless home network.  The laptop runs ubuntu and the PC runs XP.

My laptop can access the information on my PC but I can't access my Laptop from my PC.

When I go into Places and then Network I find two icons.  One relates to my laptop and the other relates to my PC.  Should there be just one icon which gives me access to both computers?

I would also like to mention that the two icons look different as well.  One says my laptop name while the other says Windows Network.  

I would appreciate any help to get both computers on the same network so that both recognise each other.

Cheers

---

### Post by Znupi on 2007-05-21
So basically, the two computers are not in the same workgroup? You can either change the PC's workgroup to MSHOME or change the laptop's workgroup to whatever the PC is set to. to do this edit your /etc/samba/smb.conf and change from workgroup = MSHOME to workgroup = <PC_Workgroup>. Then restart the samba daemons:
```

sudo /etc/init.d/samba restart

```
That should do it :). If you need any more help just ask :).

---

### Post by noMScraig on 2007-05-22
For newbies like me the two comands you need are:

sudu gedit /etc/samba/smb.conf

after you edit the file save and run

sudo /etc/init.d/samba restart

-c

---

### Post by alexcr on 2007-05-23
I am having some problem in Accessing SMB share. I changed workgroup to be the same as other PCs in my home network by editing smb.conf per the instructions in your posts. 

However, when I go to Places > Network and double click Windows Network, it says "The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network".

In WIndows, after I set the workgroup name, I should be able to browse other PCs in the same workgroup.  It seems like in Ubuntu it is not working that way.

Anyone can help me figure it out?

Thanks!

---

### Post by Znupi on 2007-05-24
Try rebooting. It happened to me, too.

---

### Post by the lemming on 2007-05-24
Just been away for a few days and just decided to solve my network problem again.

Is there any way to solve my network problems without resorting to command line magic?

I only ask because it frightens the hell out of me.

My philosophy is "Keep it simple, keep it stupid".

Cheers

---

### Post by Znupi on 2007-05-24
Well, this is the sort of thing that you can't do without command line. And it shouldn't frighten you. Not at all. Run this command in the terminal:
```

gksudo gedit /etc/samba/smb.conf

```
That will popup a window asking for your root password. Enter it, and a text editor will appear, with a text file loaded. In that file, you will see this: "workgroup = MSHOME". Change "MSHOME" to your workgroup name. Save the file (either by File -> Save or Ctrl+S) and close it.

Now run this command:
```
sudo /etc/init.d/samba restart
```
Again, you will be prompted for your root password, but directly in a terminal, no popup or anything. Just enter it (don't worry if it looks like you're not typing anything) and hit enter. You should see how it stops the Samba daemons and then starts them. Basically that's all you have to do. If after this, it still doesn't work, reboot.

---

### Post by the lemming on 2007-05-24
> **Znupi said:**
> Well, this is the sort of thing that you can't do without command line. And it shouldn't frighten you. Not at all. Run this command in the terminal:
```

gksudo gedit /etc/samba/smb.conf

```
That will popup a window asking for your root password. Enter it, and a text editor will appear, with a text file loaded. In that file, you will see this: "workgroup = MSHOME". Change "MSHOME" to your workgroup name. Save the file (either by File -> Save or Ctrl+S) and close it.

Now run this command:
```
sudo /etc/init.d/samba restart
```
Again, you will be prompted for your root password, but directly in a terminal, no popup or anything. Just enter it (don't worry if it looks like you're not typing anything) and hit enter. You should see how it stops the Samba daemons and then starts them. Basically that's all you have to do. If after this, it still doesn't work, reboot.

I followed your instructions and found that my workgroup was correctly named.

It must be something else that is wrong.  Unfortunately I can't put my finger on it.

Thanks for your help.

---

### Post by Znupi on 2007-05-24
As I understand from your first post, you can't access Ubuntu from XP, right? If so, it means there is probably a problem with the XP machine. Try pinging the Ubuntu one from the XP one, see what happens. Then try opening.... uhm... erm... oh yeah, My Computer :D, and type in the address bar
```

\\<ubuntu-machine>

```
And hit enter. See where that leads.

---

