---
title: "File sharing with Windows via Linksys Wireless Router"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by mlnease on 2009-11-25
Hello,

I connect to the internet via a Linksys wireless router, connected to our ISP via cable to my wife's computer.  I'd like to be able to share files with her computer (actually dual boot Hardy/XP) via our Motorola Surfboard router.

I've tried googling this and searching the forums and found vast quantities of data that I've so far found unhelpful.

Can anyone suggest a resource--a tutorial, maybe--to get someone started from square one who is really, utterly ignorant of networking?

Apologies if this is redundant or out of place and thanks in advance.

mike

---

### Post by bodhi.zazen on 2009-11-25
In windows , enable a shared folder

In Ubuntu connect to your Window sbox.

[http://lifehacker.com/288033/mount-a-windows-shared-folder-in-linux](http://lifehacker.com/288033/mount-a-windows-shared-folder-in-linux)

You can mount shared folders via nautilus (you do not need t use the command line, browse to places -> Network).

---

### Post by HermanAB on 2009-11-25
Well, if you are both on the same router and both use DHCP then the two machines should be in the same subnet, so you should be able to ping the other machine.  On Windows, run 'ipconfig /all' and on Linux run 'ifconfig' to see the IP addresses, then try some pings.

If the machines can ping each other then simply go and download and install FileZilla Server and Client on Windows.  You can then connect to the FileZilla server from Linux using the Nautilus file browser 'connect to server' feature in the file menu.

---

### Post by mlnease on 2009-11-25
Hi BZ,

> **bodhi.zazen said:**
> In windows , enable a shared folder

In Ubuntu connect to your Window sbox.

[http://lifehacker.com/288033/mount-a-windows-shared-folder-in-linux](http://lifehacker.com/288033/mount-a-windows-shared-folder-in-linux)

You can mount shared folders via nautilus (you do not need t use the command line, browse to places -> Network).

Thanks for this (with many other thanks from the past)--it looks great, don't have time to try it immediately but will get back to you.

mike

---

### Post by mlnease on 2009-11-25
Hi Herman,

> **HermanAB said:**
> Well, if you are both on the same router and both use DHCP then the two machines should be in the same subnet, so you should be able to ping the other machine.  On Windows, run 'ipconfig /all' and on Linux run 'ifconfig' to see the IP addresses, then try some pings.

If the machines can ping each other then simply go and download and install FileZilla Server and Client on Windows.  You can then connect to the FileZilla server from Linux using the Nautilus file browser 'connect to server' feature in the file menu.

This is all quite new to me and looks good also--I'll have a go and get back to you.  Thanks for the quick response.

Cheers,

mike

---

### Post by mlnease on 2009-11-25
Hello Again BZ,

> **bodhi.zazen said:**
> In windows , enable a shared folder

In Ubuntu connect to your Window sbox.

[http://lifehacker.com/288033/mount-a-windows-shared-folder-in-linux](http://lifehacker.com/288033/mount-a-windows-shared-folder-in-linux)

You can mount shared folders via nautilus (you do not need t use the command line, browse to places -> Network).

When I try to connect to the Windows box per the instructions from the link above (i.e. *<smb://***.***.*.***/Shared*>, I receive the following:

bash: smb://****.***.*.****/Shared: No such file or directory

Am I missing something?

Thanks again.

mike

---

### Post by mlnease on 2009-11-25
Hi Again Herman,

> **HermanAB said:**
> Well, if you are both on the same router and both use DHCP then the two machines should be in the same subnet, so you should be able to ping the other machine.  On Windows, run 'ipconfig /all' and on Linux run 'ifconfig' to see the IP addresses, then try some pings.

I ran 'ifconfig' and came up with a fair amount of code I did not understand.  I do have some vague notion of pinging (from some GUI app) but it isn't apparent to me how I can use the output of  'ifconfig' for that purpose.  (As I wrote earlier, I am truly, utterly ignorant of networking).

> **HermanAB said:**
> If the machines can ping each other then simply go and download and install FileZilla Server and Client on Windows.  You can then connect to the FileZilla server from Linux using the Nautilus file browser 'connect to server' feature in the file menu.

I have installed FileZilla on your recommendation--thanks--and look forward to figuring out how to implement it.

Thanks again for your time and patience.

mike

---

### Post by bodhi.zazen on 2009-11-25
The command you are using is very very old.

Go to places -> Connect to server

Service type : windows share
Server : windows ip address
Share : name you gave the shared folder in windows

Folder - leave blank

Use name - your windows log in name

Click connect

Enter your password on the next screen.

=====

Alternate

Open nautilus, go Places -> Home folder

Go to File -> connect to server -> enter info as above.


=====

If you wish to use the command line, 

```
sudo apt-get install smbfs
```

Now mount

```
sudo mkdir /media/windows_share
sudo mount //windows_ip/Share_name /media/windows_share /media/windows_share -o user=windows_user_name
```

See also 

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by mlnease on 2009-11-26
Thanks again for your time and assistance.

mike

---

