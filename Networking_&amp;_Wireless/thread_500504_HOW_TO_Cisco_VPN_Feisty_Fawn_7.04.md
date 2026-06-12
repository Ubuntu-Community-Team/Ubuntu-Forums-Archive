---
title: "HOW TO: Cisco VPN Feisty Fawn 7.04"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by am_pcguy on 2007-07-14
I hope this helps someone.  I've seen several other posts about installing and even patching the Cisco VPN client but I've not seen one post with the error fixes as well.  I found everything I needed it just took me 3 hours to find it all.  

First you need "[COLOR="Red"]vpnclient-linux-4.8.00.0490-k9.tar.gz[/COLOR]"  The Cisco VPN client.
Then you need to patch that client to work on Kernel 2.6.19 and above.  
I found the a patch and instructions here: [[COLOR="Navy"]http://tuxx-home.at/archives/2007/05/29/T16_34_26/[/COLOR]]("http://tuxx-home.at/archives/2007/05/29/T16_34_26/")

If you follow the instructions at that site you should now have the client patched and installed.

Next:
You need to move your profile ".pcf" file to this directory:  /etc/opt/cisco-vpnclient/Profiles/
Next make sure you can read the file with: 
```
sudo chmod 644 /etc/opt/cisco-vpnclient/Profiles/*.pcf
```
I found those solutions here: [[COLOR="Navy"]http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/[/COLOR]]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")


I had one other problem I ran into, an error that said 
"privsep: unable to drop privileges: group set failed.
The application was unable to communicate with the VPN sub-system."

I found the fix here: [COLOR="Blue"][[COLOR="Navy"]http://jason.roysdon.net/?p=780[/COLOR]]("http://jason.roysdon.net/?p=780")[/COLOR]
```
chmod 4111 /opt/cisco-vpnclient/bin/cvpnd
```

If you have more than one Network card, like a laptop with wired and wireless cards, you will need to disable the non active connection or you will get an error like "Failed to establish a VPN connection.  There are no new notification messages at this time."

Next you need to start the client .
```
/etc/init.d/vpnclient_init start
```
Then:
```
sudo vpnclient connect BLAH
```
where blah is your profile ".pcf" file.

Finally I have a working VPN Connection on my Laptop.  :)  Now I can work from home. :confused:

---

### Post by mlissner on 2007-07-14
> **am_pcguy said:**
> First you need "[COLOR="Red"]vpnclient-linux-4.8.00.0490-k9.tar.gz[/COLOR]"  The Cisco VPN client.

Forgive my ignorance, but where, pray, does one get that client? Is it commercial? Is that the deal here?

---

### Post by am_pcguy on 2007-07-14
I got it from my work.  If you go to Cisco's site you will see that you have to be some type of "registered partner" to get the client from them.  It is a pretty common vpn solution for businesses and universities, and they will provide the client to their employees / students.

---

### Post by KyleBrandt on 2007-07-14
Alternate Method:

Install vpnc: ```
sudo apt-get install vpnc
```

Convert your pfc file to vpnc config file using this perl script: [http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc]("http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc")

Edit: (Don't forget to make the script executable: chmod +x pfc2vpnc)


```
./pcf2vpnc.pl <pcf file> <vpnc config>
```

Connect: ```
sudo vpnc YourVpncConf.Conf
```

If it works for your Vpn, the advantage is open source client, and that is in the repositories..

---

### Post by mlissner on 2007-07-14
Sounds like a good strategy. 

I also discovered that if you install kvpnc, it will allow you to use a pcf file for configuration. I haven't tried that yet because I still lack such a file, but it looks like it ought to work just fine. Plus, it has a tray icon, which seems reasonable since I will be switching between one network and another.

I hate proprietary software. It makes life such a pain. Really.

---

### Post by sunken on 2007-07-15
ok, I did like this:
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

---

### Post by NilsHG on 2007-07-17
cisco installed, worked fine. restart and error. solved by disableing the networkcard currently not needed. 

i tried to get the pcf2vpnc script. "wget url" did not work (error 404) 
when i copy the code, creat a new file and make that executable will that work too?
 i am having trouble converting the .pcf to .conf ... :(
i would rather use vpnc than the cisco thing.

*edit* Problem solved. I could copy paste the source to a new file etc. the script did work then. */edit*

---

### Post by KyleBrandt on 2007-07-17
NilsHG:  Yup, I made the mistake in that post of leaving out the part where you would make the script executable: chmod +x pcf2vpnc

---

### Post by mlissner on 2007-08-11
Hmmm...I finally tried out kvpnc, and I must say, it doesn't work.

So I downloaded the pcf2vpnc script, and used it with vpnc. Now I'm getting this error:

```
sudo vpnc
vpnc: binding to 0.0.0.0:500: Address already in use

```

Any ideas? I didn't find anything in English when googling, and the French results are useless to me.

Thanks.

---

### Post by 8bit on 2007-08-17
> **KyleBrandt said:**
> Alternate Method:

Install vpnc: ```
sudo apt-get install vpnc
```

Convert your pfc file to vpnc config file using this perl script: [http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc]("http://svn.unix-ag.uni-kl.de/vpnc/trunk/pcf2vpnc")

Edit: (Don't forget to make the script executable: chmod +x pfc2vpnc)


```
./pcf2vpnc.pl <pcf file> <vpnc config>
```

Connect: ```
sudo vpnc YourVpncConf.Conf
```

If it works for your Vpn, the advantage is open source client, and that is in the repositories..

I converted my pcf file but the converted file looks much smaller and now I get the following error.
Can you help me?
vpnc: hash comparison failed:  (ISAKMP_N_AUTHENTICATION_FAILED)(24)
check group password!

There is no group password in the file. What am I missing?

---

### Post by KyleBrandt on 2007-08-18
Sounds like the script failed, maybe you will just have to manually create the config file.

---

### Post by bogr@ on 2007-08-19
My company uses a VPN from F5 ([www.f5.com](www.f5.com)) and I'm wondering how to get this working with Ubuntu.  There are a number of work applications that I can't access and have to keep going back to windows to get what I need.
Any help much appreciated,
Thanks.

---

### Post by lynchman on 2007-08-20
Wow - vpnc worked perfectly on the first try.  Thanks! :)  (not that I'm happy to now work from home, but at least I don't have to use XP in vmware...)

---

### Post by lynchman on 2007-08-20
> **mlissner said:**
> 
Now I'm getting this error:

```
sudo vpnc
vpnc: binding to 0.0.0.0:500: Address already in use

```


I get that error if I run it as a regular user, and not with sudo.  Try it with sudo and see if it works (anyone know how to get this to run w/out sudo?)

I also tried kvpnc but I can't get it to connect.  But the console is perfect.

---

### Post by peteguhl on 2007-09-05
Since my school uses certificate based vpn, I cannot use vpnc...  so I've been fooling with this little bugger for several days straight now and I think I've got a couple tips that'll help a few folks....

First, remove or move your old profiles and certificates (just to make sure we start from scratch)
```
sudo mv /etc/opt/cisco-vpnclient ~/cisco-vpnclient.bak
```

Allow non-root users to connect via vpnclient:
```
sudo chmod 4755 /opt/cisco-vpnclient/bin/cvpnd
```

Enable autostart of vpnclient_init:
```
sudo update-rc.d vpnclient_init start 60 S .  
```

cisco_cert_mgr will probably crash if you try to import a root certificate with a filename longer than 6.3 (123456.pfx)

Also, the Root certificate must be installed as the root user, but user
certificates can be installed by any user as long as the /etc/opt/...
directory permissions are left alone

Couple errors with resolutions:
>  
Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.
Make sure all network connections are set to "Roaming
mode" as there is an issue with Zeroconf... this took me awhile to figure out...

> 
The profile specified could not be read.

```
sudo chmod 644 /etc/opt/cisco-vpnclient/Profiles/*.pcf
```

---

### Post by Dirren on 2008-05-15
Thanks sunken,

That piece of information really helped.
I installed vpnc, created the configfile from the pcf-file according to your instructions, fired up vpnc and tadaa, it worked.

I've been using the Cisco client for quite some time but, apart from not being open source, it bugs me to have to reinstall the thing whenever I get a kernel update!
From what I understand vpnc runs in user-mode and does not suffer from this "deficiency".

---

