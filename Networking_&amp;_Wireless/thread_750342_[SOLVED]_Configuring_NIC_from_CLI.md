---
title: "[SOLVED] Configuring NIC from CLI"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Terminating.proprietary on 2008-04-09
Trying to put Ubunutu on an older pc. Due to the age of the computer I was forced to do an initial server or basic install of the OS planning to follow up with 
```
sudo apt-get install ubuntu-desktop
```
Thing is without a GUI I am not so sure how to set up the NIC. So I do have a general idea.
I need to use ifconfig right? So I do that and see that there is no network traffic on eth1 which I assume is the NIC, there is also something titled lo I am assuming that is the winmodem that came with the pc which is not used I am not so sure though. From what I have read I need to configure a file called /etc/network/interfaces correct? I have read some documentation on what I need to enter although I am still not so sure so any help there will be appreciated. The major problem comes when I actually try to edit the file. I read to type```
 sudo vi /etc/network/interfaces
``` to edit the file. This has me edit the file with vim editor correct? I do not know exactly where to enter the info though and when I try to type nothing really happens, I think maybe I just do not know how to properly use the editor, I am really new to ubuntu and linux so yea. I only know what vim and emacs are from a bit of reading and do not really understand the concept. Typing shopt -o shows vim as off yet the documentation I read told me to type sudo vi /etc/network/interfaces could this be a conflict? PLease save me. I just want to know what to enter to configure my NIC I am using a router and How to enter it.

---

### Post by Eiríkr on 2008-04-09
If you want vim, you have to use "vim" instead of "vi".  There's a few useful online cheat sheets for vim; the one I use most is [here]("http://www.tuxfiles.org/linuxhelp/vimcheat.html"), and Google pulls up [these]("http://www.google.com/search?q=vim+cheat+sheet").  

Note that when you first open vim, it's in command mode.  To enter editing (insertion) mode, either hit the Insert key or the I key.  To go back to command mode, hit Escape.

As to what to enter into your /etc/network/interfaces file, it depends on your setup.  Are you wireless, or wired?  Static IP, or dynamic?

Sample wired dynamic IP setup:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Sample wired static IP setup:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
```

The gateway should be the address of your router.

HTH,

Eiríkr

---

### Post by dstew on 2008-04-09
I like **nano** for a command-line text editor. It has a "menu" at the bottom that you use.

It would be nice to see the ouptut your ifconfig command. You can redirect the output to a text file, then copy that over to your network-connected computer to post on the forum:```
ifconfig > ifconfig.txt
```The output will be in a file named ifconfig.txt that you can open with any text editor.

---

### Post by Terminating.proprietary on 2008-04-09
Thing is it is a friends pc so I am getting in touch with him now and will be hading over there to try and follow these instructions. I am not entirely sure how i am going to export the file to a USB device or another hardrive. Further instructions wopuld be greatly appreciated.

---

### Post by Terminating.proprietary on 2008-04-09
> **Eiríkr said:**
> If you want vim, you have to use "vim" instead of "vi".  There's a few useful online cheat sheets for vim; the one I use most is [here]("http://www.tuxfiles.org/linuxhelp/vimcheat.html"), and Google pulls up [these]("http://www.google.com/search?q=vim+cheat+sheet").  

Note that when you first open vim, it's in command mode.  To enter editing (insertion) mode, either hit the Insert key or the I key.  To go back to command mode, hit Escape.

As to what to enter into your /etc/network/interfaces file, it depends on your setup.  Are you wireless, or wired?  Static IP, or dynamic?

Sample wired dynamic IP setup:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Sample wired static IP setup:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
```

The gateway should be the address of your router.

HTH,

Eiríkr

Thanks a ton, since it isn't my network i will probably just keep it dynamic. As far is vi can I use vi is it an editor? I got the whole vi idea from here [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)
I am leaving for my friends house now about a 15 minute walk and I will use my laptop to access this forum. I think I may try the vim editor and use that cheat sheet since I now know exactly what to enter. What is up with these wacky ediotrs anyhow?

---

### Post by dstew on 2008-04-09
> What is up with these wacky ediotrs anyhow?They come from the very old Unix programs, which had small executable files. That was very important in the days when memory was expensive. Now, memory is relatively cheap, and larger text editors are not a problem. But lots of the old guard still like vi, vim, emacs and those old editors, because they are used to them. They are actually pretty fast once you are trained. I tried to learn vi at one time, but now I just use nano.> I am not entirely sure how i am going to export the file to a USB deviceYou should find the directory for the USB drive in the /media directory. If the USB drive has a volume name, that will be the name of the directory in /media that has the USB drive root directory in it. Use the cp (copy) command to copy the file to the directory, like this:```
cp ifconfig.txt /media/usb_volume_name
```To look in the directory for the real name, use the ls (directory list) command```
ls -l /media
``` See [this site]("http://www.linuxcommand.org/learning_the_shell.php") for learning commands. You can also use the man (manual) pages to get information about commands. For instance, if you want to know what the cp command is, enter```
man cp
```Entering help on the command line gives a list of commands, then you can use the man pages to figure out what they do.

---

### Post by Eiríkr on 2008-04-09
If your friend's computer has ssh installed, and if your laptop will be connecting to your friend's LAN via his router, it might be easier to just ssh into his machine and run ifconfig there in your terminal on your laptop, where you can copy directly into a post here, rather than having to muck about with copying the file to a USB stick.

In a terminal window on your laptop:
```
ssh USERNAME@IP.ADD.RE.SS
```
Use your friend's username, if he's amenable to you logging in as him.  The IP address would of course be the address of the machine you're connecting to.  

HTH,

Eiríkr

---

### Post by Terminating.proprietary on 2008-04-09
working on it i will get that output in a minute thanks a lot

---

### Post by Terminating.proprietary on 2008-04-09
> **dstew said:**
> They come from the very old Unix programs, which had small executable files. That was very important in the days when memory was expensive. Now, memory is relatively cheap, and larger text editors are not a problem. But lots of the old guard still like vi, vim, emacs and those old editors, because they are used to them. They are actually pretty fast once you are trained. I tried to learn vi at one time, but now I just use nano.You should find the directory for the USB drive in the /media directory. If the USB drive has a volume name, that will be the name of the directory in /media that has the USB drive root directory in it. Use the cp (copy) command to copy the file to the directory, like this:```
cp ifconfig.txt /media/usb_volume_name
```To look in the directory for the real name, use the ls (directory list) command```
ls -l /media
``` See [this site]("http://www.linuxcommand.org/learning_the_shell.php") for learning commands. You can also use the man (manual) pages to get information about commands. For instance, if you want to know what the cp command is, enter```
man cp
```Entering help on the command line gives a list of commands, then you can use the man pages to figure out what they do.

I used ```
 ls -l /media 
``` with the usb flash drive in and with it out and got the same output is there another way to identify it? Some text cam up when i inserted the drive looked like this
```
[ 1652.516377] cd 3:0:0:0: [sbd] Assuming drive cache: write through
```
below it says that again.

---

### Post by chili555 on 2008-04-09
I think you want vim, not vi. Make changes after pressing 'INSERT', get out of the edit mode by pressing 'ESC.' Save your changes with :wq  which stands for 'write and quit.' Quit without making any changes with :q!

I have used vim for years, including on remote machines with ssh and writing scripts, and that's all the vim I know or want. Vim is powerful in that you do not need a desktop or graphical interface running, you can edit on a remote machine with ssh and it's light and quick. Once you've used vim, it seems very slow to me to use gedit or kate.

---

### Post by Terminating.proprietary on 2008-04-09
also when I go to edit the /etc/network/interfaces file I get some message about swap files and blah blah so I do what is says and type vim -r /etc/network/.interfaces and that lists three files and I do not know what it is talking about do i need to delete these swap files?

---

### Post by Terminating.proprietary on 2008-04-09
Good news I got the connection working. I am downloading the ubuntu-desktop package now

How to mArk as solved?

---

### Post by chili555 on 2008-04-09
I have tried but been unable to reproduce this. If you simply do:```
sudo vim /etc/network/interfaces
```Can you bypass or skip all the questions and just edit the file? Don't forget to save as I outlined above.> do i need to delete these swap files?No.They do no harm and may come in handy to restore a backup.

---

### Post by Eiríkr on 2008-04-09
@chili555 --

Terminating.proprietary has already fixed the issue, so your post would seem to come a little late.  Besides, such swap file issues only occur when other processes have opened a file for editing and are either still active or quit uncleanly, so it's no surprise at all that you would not be able to reproduce his symptoms.  If you'd like to for some reason, simply open multiple terminals, and type **sudo vim /etc/network/interfaces** into all of them.  The second, third, and so forth should complain.  

----------

@Terminating.proprietary --

You can mark any thread you started as SOLVED in the Thread Tools dropdown towards the top-right  of the page.  

Cheers,

Eiríkr

---

