---
title: "Wi-Fi either disconnects or ask for password immediately"
date: 2017-11-27
forum: Networking &amp; Wireless
---

### Post by edwjusti on 2017-11-27
I have been facing a lot of problems trying to run ubuntu on my laptop (Acer ES1-533-C27U), and one of these if the unstable wifi. I have tried all methods trying to solve this, but none of them worked, the best that I got was a connection during 30 seconds and without internet access on kernel 4.10, on 4.14 it doesn't connect at all. As last hope I am posting this thread to try to find some help :cry:

---

### Post by jeremy31 on 2017-11-27
Please see the wireless script link in my signature and post results

---

### Post by edwjusti on 2017-11-27
> **jeremy31 said:**
> Please see the wireless script link in my signature and post results
Ok, here it is:

---

### Post by jeremy31 on 2017-11-28
If you can make changes to the wifi router settings, move it to channel 3 and change encryption to WPA2 AES only

---

### Post by edwjusti on 2017-11-28
I changed the router configuration as suggested, and still no successful connection.

---

### Post by jeremy31 on 2017-11-28
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
systemctl restart network-manager.service
```
This will keep network manager from trying to enable wifi power management.  I see you have a command in /etc/pm/power.d/wireless but network manager will ignore it

---

### Post by edwjusti on 2017-11-28
I tried that but it didn't connect on the latest kernel, so I went back to 4.10, but it didn't stay connect for more than 2 minutes, and while I was connected I had no access to internet, not even the hosts in the same network.

---

### Post by edwjusti on 2017-12-01
I don't want to keep bothering in this thread, but do you know if there is anything else I could try?
It really sucks not being able to move around with my laptop :/
When I first decided to install ubuntu I thought this distro, like many others, was mature enough in terms of things working out of the box, but it seems that the ghost that scared users and their exotic hardware is still around in the linux world (Although my hardware seems pretty common).

This laptop came with windows preinstalled and I really don't want to download more than four GBs of spyware to get my wifi working :-(

---

### Post by wildmanne39 on 2017-12-01
> **edwjusti said:**
> I tried that but it didn't connect on the latest kernel, so I went back to 4.10, but it didn't stay connect for more than 2 minutes, and while I was connected I had no access to internet, not even the hosts in the same network.

From the new kernel try:
```
sudo dpkg-reconfigure resolvconf
```
then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" then reboot if it does not connect please post a new script from the 4.10 kernel.

---

### Post by edwjusti on 2017-12-02
> **wildmanne39 said:**
> From the new kernel try:
```
sudo dpkg-reconfigure resolvconf
```
then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" then reboot if it does not connect please post a new script from the 4.10 kernel.
It did not connect this time.

---

### Post by wildmanne39 on 2017-12-02
The following is still incorrect:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.0.1
search localhost
```
The google dns servers should not be in this file, I to use google servers but they do not show up in that file, did you add them again after you ran the command I gave you? Did you run the command on the 4.10 kernel or the new kernel?
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

This is all that should be in that file for the kernel:
```
nameserver 127.0.0.53
```
That is not what we see either.

---

### Post by edwjusti on 2017-12-02
> **wildmanne39 said:**
> The following is still incorrect:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.0.1
search localhost
```
The google dns servers should not be in this file, I to use google servers but they do not show up in that file, did you add them again after you ran the command I gave you? Did you run the command on the 4.10 kernel or the new kernel?
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

This is all that should be in that file for the kernel:
```
nameserver 127.0.0.53
```
That is not what we see either.

I had edited myself the head file in /etc/resolvconf/resolv.conf.d to see if it helped, so that's why the configuration looks like that, I returned the original head file configuration, but it still doesn't work.
I completely lost my hopes in this, I watch the logs and I see that NetworkManager behavior is simply non sense, it connects then disconnects asking for the password, timing out, reconnecting, etc... 
Could this be simply a bad implemented driver or NetworkManager bug?

---

### Post by wildmanne39 on 2017-12-02
Is this in that file?
```
nameserver 127.0.0.53
```
I believe that should be in that file if you are using 4.10 kernel and above and not the other nameserver. It gets hard when you upgrade kernels at sometimes or upgrade operating systems instead of doing a clean install. The script still shows channel one, you should try channel 3 like jeremy suggested, set it to manual selection and not auto so it does not change every time it connects. If it does not help post a new script file please.

We have made some changes that should work around the network manager bugs for this kernel and driver. 

Thanks

---

### Post by edwjusti on 2017-12-02
> **wildmanne39 said:**
> Is this in that file?
```
nameserver 127.0.0.53
```
I believe that should be in that file if you are using 4.10 kernel and above and not the other nameserver. It gets hard when you upgrade kernels at sometimes or upgrade operating systems instead of doing a clean install. The script still shows channel one, you should try channel 3 like jeremy suggested, set it to manual selection and not auto so it does not change every time it connects. If it does not help post a new script file please.

We have made some changes that should work around the network manager bugs for this kernel and driver. 

Thanks
No, there are only comments in the head file, this is the content of /etc/resolv.conf generated by resolvconf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search domain.name

```

The funny is that this looks like the default router configuration, but I already have configured the dns on my router and even the network profiles of network manager, but it keeps adding this defaults. And just now I reliased that those changes I had made in /etc/resolvconf/resolv.conf.d/head were allowing me to access internet through wired connection, but with the plain resolvconf defaults it doesn't work since those are  invalid servers.

---

### Post by edwjusti on 2017-12-02
Removing the package resolvconf seems to help at least with the wired connection, network manager is also adding some defaults in the symlink /etc/resolv.conf, but the nameserver 127.0.1.1 works.

---

### Post by wildmanne39 on 2017-12-02
My computer does not want to open that file this time it refuses would you please post the file on pastebin.

Thanks

---

### Post by jeremy31 on 2017-12-02
wildmanne39, I copied it over [http://paste.ubuntu.com/26098631/](http://paste.ubuntu.com/26098631/)

---

### Post by wildmanne39 on 2017-12-02
Thanks jeremy, you can jump back in if you want too.
> Removing the package resolvconf seems to help at least with the wired connection, network manager is also adding some defaults in the symlink /etc/resolv.conf, but the nameserver 127.0.1.1 works.
You completely removed the package resolvconf or did you just edit the file?

It shows you are connected but I am guessing you do not have internet on the wifi connection though?

I still think you should try:
```
nameserver 127.0.0.53
```
in the file since you are using the 4.10 kernel but it might not be mandatory when you do an upgrade, when you do a clean install to the OS that uses the 4.10 kernel resolvconf has nameserver 127.0.0.53 in the file I know that for sure. You will remove the nameserver that is in there now and add the new one, also you can only use network manager or wicd because they conflict with each other so I suggest you remove one of them, usually I say keep network manager because wicd has not been maintained in a very long time.

---

### Post by edwjusti on 2017-12-02
> **wildmanne39 said:**
> Thanks jeremy, you can jump back in if you want too.

You completely removed the package resolvconf or did you just edit the file?

It shows you are connected but I am guessing you do not have internet on the wifi connection though?

I still think you should try:
```
nameserver 127.0.0.53
```
in the file since you are using the 4.10 kernel but it might not be mandatory when you do an upgrade, when you do a clean install to the OS that uses the 4.10 kernel resolvconf has nameserver 127.0.0.53 in the file I know that for sure. You will remove the nameserver that is in there now and add the new one, also you can only use network manager or wicd because they conflict with each other so I suggest you remove one of them, usually I say keep network manager because wicd has not been maintained in a very long time.
The edit I refered to was that one that made the google nameserver be appended in the resolv.conf as seen in one of the previous logs, but yes I purged the package, the package uninstallation helped by not appending those invalid directives in the resolv.conf and this at least made the internet work properly again on wired connection.

I will try to append this address manually since resolvconf was not doing it by default, but I will do it tomorrow, it is already late and I also don't want to punch through my laptop screen of rage :'D
It is the second ubuntu distro that I installed that has this same bug, I even tried elementary os in live mode today, and again, the wifi did not work out of th box...
I guess that installing fedora won't make any difference, they use network manager too, right?

And also thank you guys for taking your time to help me with this problem! It might take sometime but the wifi will work, hehe

---

### Post by edwjusti on 2017-12-03
I know that wicd is not being maintained, but ironically in one of my tests this client was able to connect me to wifi and with internet access, the speed was terrible though.
Since we can agree now that the problem with wifi on kernel 4.10 is simply dns, and can be solved making the client add the valid server, it seems solved, but what about the wifi not connecting at all on kernel 4.14+?
I updated my kernel because it solved a problem with the suspend feature, basically I can't suspend the computer when the lid is open on kernel 4.10, and there is also a problem with the shutdown process, the system hangs at "Reached target shutdown", apparently because of this 'Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug', so I am forced to use that flag, but whatever this is going off-topic, but what I want to say is that linux is definitely not made for this laptop xD

---

### Post by wildmanne39 on 2017-12-03
I am not sure what is going on with the kernel 4.14 but I see this in the file for that kernel:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.0.1
```
for clarification is wifi working with the file with this nameserver?
```
nameserver 127.0.0.1
```
Or the one I think is needed in 4.10 and above kernels?

---

### Post by edwjusti on 2017-12-04
> **wildmanne39 said:**
> I am not sure what is going on with the kernel 4.14 but I see this in the file for that kernel:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 127.0.0.1
```
for clarification is wifi working with the file with this nameserver?
```
nameserver 127.0.0.1
```
Or the one I think is needed in 4.10 and above kernels?
On kernel 4.10 the wifi connects but there is no internet access, and the resolv.conf file no longer has this format, this is the current content:
```

# Generated by NetworkManager
nameserver 127.0.1.1

```
Only wired has internet access though.
On kernel 4.14 wifi don't even connect.

---

### Post by wildmanne39 on 2017-12-04
Reset your router and after it is back up remove all connections from network manager then reboot and let network manager find your network, then enter credentials.

---

### Post by edwjusti on 2017-12-05
> **wildmanne39 said:**
> Reset your router and after it is back up remove all connections from network manager then reboot and let network manager find your network, then enter credentials.

I already did a reset, and also removed the connections, but it still doesn't work.
Well, I think I should report a bug.

---

