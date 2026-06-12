---
title: "Windows 10 installation broke my network connection"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2016-01-05
I used Ubuntu 14.04 on a homemade AMD computer, linked by Ethernet to my wife's Dell desktop. I switched hers from Windows 7 to Windows 10 and it created a problem. Previously, the two had shared files easily. Now neither one recognizes the other. I'm sure it is a Windows problem, but does anyone have a way I can diagnose and possibly fix it from the Linux machine? It "sees" the Windows Network and the PC, but can't get down to the folders that contain the docs and pix. From the PC side, it can't even see the Linux computer.

---

### Post by Morbius1 on 2016-01-05
> From the PC side, it can't even see the Linux computer.         
At the moment Win10 can't see anything on the home network. It can't even see itself half the time: [https://social.technet.microsoft.com/Forums/en-US/2131750e-d589-41f0-b6a3-1c7dac2361d9/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10-after-update](https://social.technet.microsoft.com/Forums/en-US/2131750e-d589-41f0-b6a3-1c7dac2361d9/cannot-connect-to-cifs-smb-samba-network-shares-shared-folders-in-windows-10-after-update)

If you follow that thread you will note that what's all the rage now is to alter the internals of Win10 so that you revert SMB back to where it was when Windows 2000 was king. Insanity. Microsoft  is aware of the problem and there should be a fix sometime in the future - maybe.

Anyway, the issue is the ability of WIn10 to "browse" the network not it's ability to connect to another host - you just have to do it manually:

On Win10 open Run ( WinKey+R ) and enter:
```
\\linux-host-name
```
Win10 now does mDNS ( which Ubuntu does by default ) so you can also run it this way:
```
\\linux-host-name.local
```
[COLOR=#0000cd][I]In both cases linux-host-name is your host name on the linux box.
[/I][/COLOR]

---

### Post by Lloydb39 on 2016-01-05
I went poking around to make sure what my hostname is and found this in syslog. What does it mean?
linux kernel: [289261.846925] systemd-hostnamed[1313]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

---

### Post by weatherman2 on 2016-01-05
You don't even need to use hostname to access the files - you can simply use the IP address (as long as the IP address doesn't change). In Linux in a terminal type:

ifconfig

to find out your Linux machine's IP address.  Then on the Windows machine run

\\192.168.1.2

(replace "192.168.1.2" with your actual IP address)

---

### Post by Morbius1 on 2016-01-06
> I went poking around to make sure what my hostname is.....
Just open a terminal. Your host name is to the right of the @ sign.

Or just run:
```
hostname
```

And:
>  Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname
I have no idea what that's all about. And "nss-myhostname" appears to be an improperly labelled library.  I will investigate when I get a chance.

[COLOR=#0000cd]**EDIT**[/COLOR]: the nss-myhostname warning appears to be a bug: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1277608](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1277608)

---

### Post by Lloydb39 on 2016-01-06
Apparently my hostname is linux. so i tried linux-linux on the Windows Run command line. It couldn't be found and running diagnostics said my DNS server might not be available.

---

### Post by Morbius1 on 2016-01-06
If your host name is linux the command from windows is:
```
\\linux
```
Or:
```
 \\linux.local
```

---

### Post by Lloydb39 on 2016-01-06
Tried that, didn't work. Diagnostics said "one or more network protocols is missing." For the earlier error message I flushed my DNS. Didn't help either. Seems like this is a current Windows problem for which they have no fix.

---

### Post by Morbius1 on 2016-01-06
Welcome to the wacky world of Windows 10.

I'd go with weatherman2's suggestion of using the ip address first. 

I take it you have searched the usual places for this like technet ( [https://social.technet.microsoft.com/Forums/en-US/65d6da9c-f6f9-4c56-9a85-2c1e4727a0d6/missing-one-or-more-network-protokols?forum=win10itpronetworking](https://social.technet.microsoft.com/Forums/en-US/65d6da9c-f6f9-4c56-9a85-2c1e4727a0d6/missing-one-or-more-network-protokols?forum=win10itpronetworking) ) or the windows 10 forum ( [http://www.tenforums.com/network-sharing/35400-one-more-network-protocols-missing-computer-error.html](http://www.tenforums.com/network-sharing/35400-one-more-network-protocols-missing-computer-error.html) ).

Sorry, I've lived through a number of road blocks with Win10 updates but so far that one hasn't happened to me ..... yet.

---

### Post by Lloydb39 on 2016-01-06
Well, here's a twist. I opened File Explorer, typed "\\linux.local" in the bar and it found the documents and pictures on my Linux machine! Presumably, it will stay there. I'm marking this solved. Thanks for the help.

---

### Post by Lloydb39 on 2016-01-08
I posted this earlier and marked it solved, but really only solved half the problem. I am still unable to access files on my Windows 10 computer from my Ubuntu 14.04 computer, as I could before I replaced Windows 7 with Windows 10. They are connected by Ethernet. No wireless problem. Ubuntu can ping the other computer, and shows the network and workgroup as mounted, but can't get past that to other subfolders that are shared. It asks for a password, and doesn't take anything I put in. (I don't know what the password is, have never been asked for it, don't know where to find it and the Windows "experts" online say Workgroup doesn't have a password. Go figure.) I've looked at the Samba conf file and haven't found anything that looks suspicious. Should I undo and re-install Samba, and how? Or is there another easy way to crack this problem? Thanks. (I got the title wrong and couldn't change it. Should be "accessing Windows 10")

---

### Post by howefield on 2016-01-08
Duplicate threads merged.

---

### Post by Morbius1 on 2016-01-08
I wouldn't reinstall samba.

If you set up your old share to allow anonymous guest access that likely won't work with Win10 since it disables it.

There's a registry hack to "fix" that and if I can find it I'll post a link. I generally don't like registry changes on Windows especially for something like this so what I always do is create a user on Windows. I call him/her/it smbuser and I give it the password of smbuserpw ( note: I'm not very creative ). Then I make sure smbuser has access on the Windows end to the folder being shared.

When Windows asks for credentials I pass smbuser / smbuserpw.

---

### Post by Lloydb39 on 2016-01-08
I think I allowed "everyone" access. Don't remember seeing anonymous. Is there a share setting on Windows 10 that will work? Or is it just a "thing"?

---

### Post by Morbius1 on 2016-01-08
"everyone" on Windows has never meant everyone. It's always meant every local user on the Windows system. Windows has always had a love / hate relationship with the guest account so on some versions it's enabled by default so it falls under the "everyone" classification but on others it does not.

Here's the promised link: [http://www.dedoimedo.com/computers/windows-10-network-share-access.html](http://www.dedoimedo.com/computers/windows-10-network-share-access.html)

There may be a way to do this through settings but I'm not sure. And I've never resorted to using this since as I said above it's not something I would do. This isn't OSX or Linux after all so if Windows doesn't do this by default they must have a reason.

In any event this is purely a Windows issue and best discussed in a Windows forum I would think.

---

