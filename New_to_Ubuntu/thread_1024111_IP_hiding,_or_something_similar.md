---
title: "IP hiding, or something similar"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-28
I will be going to China soon, and i know some webpages are either blocked by the government, or users from chinese ip addresses are blocked by the websites. Is there something i can do to get around these hurdles?

---

### Post by StOoZ on 2008-12-28
yes , use a proxy server when surfing the web , it will be slower than the native speed

---

### Post by Falc7 on 2008-12-28
I did some research about proxies. Tor button and Foxyproxy seem good, but i have run into trouble with both of them. With Tor button, no web pages load, i just get this message
[http://img139.imageshack.us/my.php?image=screenshotjv6.png](http://img139.imageshack.us/my.php?image=screenshotjv6.png)

And with foxyproxy, i chose use default proxy for all url. But when i go to a 'whats my ip address' web site. I get the same ip address reported whether or not i turn foxy proxy on :confused:

---

### Post by teddks on 2008-12-28
The best solution is [Tor](http://torproject.org).. Tor is a low-latency anonymity network that provides an anonymous interface to TCP services. The chinese government has not succeeded in blocking Tor, and a lot of Chinese activists use it, including Free Tibet protesters during the Olympics.

You can install Tor on Ubuntu via the usual means. You'll also want to install Privoxy, a filtering HTTP proxy, and the NoScript plugin for Firefox. Privoxy blocks adds and content which could compromise your anonymity (allowing the Chinese to figure out who and where you are) and NoScript blocks all client-side script including javascript, Java, and Flash (which also can compromise your anonymity).

Here are apturl links for easy installation:
[Tor](apt://tor)
[Privoxy](apt://privoxy)
[NoScript](apt://mozilla-noscript)

You should set up a different firefox profile for Tor use. Don't use Torbutton -- this encourages you to mingle anonymous and non-anonymous browsing in ways which could be unsafe. To do that, start firefox from the command line with the -ProfileManager argument. The command line is:
```
firefox -ProfileManager
```

When you create a new profile for firefox, make an icon to launch it. Pick a different picture and alt-text for the icon, and make the command:```
 firefox -P <profile name goes here>
```

To secure the new profile, go into Edit>Preferences and disable cache and history. Set the offline data storage size to 0MB, and tell it to wipe cookies, history, offline website data, and authenticated sessions. Set the cookie preferences to default deny, and add hosts that you trust to the "exception" list. I also recommend installing [ForceHTTPS](http://forcehttps.com/), as Tor exit nodes are capable of reading any traffic you put through them that isn't encrypted.

If you're running Intrepid Ibix, you can increase your (already rather secure) setup's security by creating an encrypted ~/Private directory, with this command:
```
ecryptfs-setup-private
```

This will create a directory which is unlocked automatically at login, but without your password, will be nothing but encrypted data. Move your firefox profile into that directory by:
[list=#]
[*]Viewing hidden files in nautilus (control-H) and going into the ~/.mozilla/firefox directory
[*]Now, move the folder to your ~/Private directory.
[*]Right click the folder (that is now in your ~/Private directory) and select "Make Link".
[*]Move the link to your ~/.mozilla/firefox directory, and rename it to remove the "Link to " text.
[/list]
Now, firefox will transparently access the encrypted folder. To remove all evidence of the anonymous profile, just delete that link and the desktop icon.

I understand this is a bit long for an ostensibly simple question, but anonymity is complex, and if you're going to be going up against the Chinese secret police, you need to be as secure as possible. Good luck.

---

### Post by Falc7 on 2008-12-29
> **teddks said:**
> 
When you create a new profile for firefox, make an icon to launch it. Pick a different picture and alt-text for the icon

Thanks for your post. How do i make a new icon? There didn't seem to be an option in the profile manager

---

### Post by cariboo on 2008-12-29
You may want to have a look at this [manual]("http://en.flossmanuals.net/CircumventionTools") called How to Bypass Internet Censorship.

Jim

---

### Post by teddks on 2008-12-29
> **Falc7 said:**
> Thanks for your post. How do i make a new icon? There didn't seem to be an option in the profile manager

That's outside FireFox. Right click on the desktop and select "Create Launcher" (or click on the menu bar and select "add to panel", then "custom application launcher").  Put in a value for the name and comment, then for the "Command" field, put in:
```
firefox -P <profile name here> -no-remote
```

The -P argument specifies the profile, the -no-remote argument tells it not to connect to an existing instance of firefox, so you can launch both profiles at the same time. Change your existing Firefox icon to have the command:

```
firefox -P <default profile name here> -no-remote
```

And since the FLOSS Manuals manual was linked, it'd be good to tell you that you should definitely read the chapter on Tor Bridges as that will help you avoid detection inside China.

---

### Post by Falc7 on 2008-12-30
Thanks for the tips and links guys, i've set that up. One thing i've noticed however is that my ip address is reported as the same number (from a 'whats my ip address?' website), no matter which firefox profile i use, is that normal?

---

### Post by teddks on 2008-12-30
> **Falc7 said:**
> Thanks for the tips and links guys, i've set that up. One thing i've noticed however is that my ip address is reported as the same number (from a 'whats my ip address?' website), no matter which firefox profile i use, is that normal?

No, that is incredibly abnormal. However, I don't think I've mentioned how to specifically set up Tor for the anonymous profile, and if you haven't done that, you haven't really done anything. The Tor docs regarding that are [here](https://www.torproject.org/docs/tor-doc-unix.html.en), but they don't go over manually configuring firefox proxy settings. Since we aren't using Torbutton, we need to do that ourselves.

Go to Edit>Preferences>Advanced>Network, and select the button "Configure how Firefox connects to the network". Set every "<Whatever> Proxy" value to localhost with the port 8118, and for "Socks Host" set the host to localhost and port to 9050.

Another thing I forgot to mention: Go to Tools>Addons>Plugins in the anonymous profile and install all the plugins except the printing one. No flash, no multimedia, nothing. Having those plugins increase the "surface area" of potential attacks.

To check your setup, go to [http://decloak.net/](http://decloak.net/) and run the test. If anything besides a Tor IP and a DNS server comes up, you haven't finished yet.

---

### Post by Falc7 on 2008-12-30
Looking in that link you gave me [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)
It says:
Open Privoxy's "config" file (look in /etc/privoxy/ or /usr/local/etc/) and add the line
forward-socks4a / 127.0.0.1:9050 .
to the top of the config file. Don't forget to add the dot at the end. 

I found that file, but it seems more like a 'how to guide'. It starts like this:

```
#        Sample Configuration File for Privoxy
#
#  Id: config,v
#
#  Copyright (C) 2001-2008 Privoxy Developers http://www.privoxy.org/
#
####################################################################
#                                                                  #
#                      Table of Contents                           #
#                                                                  #
#        I. INTRODUCTION                                           #
#       II. FORMAT OF THE CONFIGURATION FILE                       #
#                                                                  #
#        1. LOCAL SET-UP DOCUMENTATION                             #
#        2. CONFIGURATION AND LOG FILE LOCATIONS                   #
#        3. DEBUGGING                                              #
#        4. ACCESS CONTROL AND SECURITY                            #
#        5. FORWARDING                                             #
#        6. WINDOWS GUI OPTIONS                                    #
#                                                                  #
####################################################################
#
```

It dosen't seem right to just stick they say the line they say at the above this table.

---

### Post by teddks on 2008-12-30
It doesn't seem right, but it is. It's just a configuration file.

---

### Post by Falc7 on 2008-12-30
great, thats all set up, they now give completely different ip addresses. Thanks!

---

### Post by teddks on 2008-12-30
> **Falc7 said:**
> great, thats all set up, they now give completely different ip addresses. Thanks!

Great. What does the [Decloak Engine](http://decloak.net) say?

---

### Post by Falc7 on 2008-12-30
```
Field	Data	Dependency
External Address 	85.25.151.22	Browser
Internal Host 	unknown	Java
Internal Address 	unknown	Java

DNS Server (Java) 	unknown	Java
DNS Server (HTTP) 	unknown	Browser
DNS Server (Word) 	unknown	Office
DNS Server (iTunes) 	unknown	iTunes
DNS Server (Quicktime) 	unknown	Quicktime

External NAT (Java)	unknown	Java
External NAT (Flash)	91.84.68.247	Flash
External NAT (Word)	unknown	Office
External NAT (iTunes)	unknown	iTunes
External NAT (Quicktime) 	85.25.151.22	Quicktime

```

---

### Post by teddks on 2008-12-30
> **Falc7 said:**
> ```
Field	Data	Dependency
External Address 	85.25.151.22	Browser
Internal Host 	unknown	Java
Internal Address 	unknown	Java

DNS Server (Java) 	unknown	Java
DNS Server (HTTP) 	unknown	Browser
DNS Server (Word) 	unknown	Office
DNS Server (iTunes) 	unknown	iTunes
DNS Server (Quicktime) 	unknown	Quicktime

External NAT (Java)	unknown	Java
External NAT (Flash)	91.84.68.247	Flash
External NAT (Word)	unknown	Office
External NAT (iTunes)	unknown	iTunes
External NAT (Quicktime) 	85.25.151.22	Quicktime

```

It's bad that you have that data from Quicktime and Flash. Have you disabled the plugins for those? Uninstalling them on the anonymous profile won't uninstall them on the normal one.

---

### Post by Falc7 on 2008-12-31
oops, i forgot to do that. They are disabled now, and this is the info i get 

```
Field	Data	Dependency
External Address 	85.25.152.185	Browser
Internal Host 	unknown	Java
Internal Address 	unknown	Java

DNS Server (Java) 	unknown	Java
DNS Server (HTTP) 	unknown	Browser
DNS Server (Word) 	unknown	Office
DNS Server (iTunes) 	unknown	iTunes
DNS Server (Quicktime) 	85.25.255.10	Quicktime

External NAT (Java)	unknown	Java
External NAT (Flash)	unknown	Flash
External NAT (Word)	unknown	Office
External NAT (iTunes)	unknown	iTunes
External NAT (Quicktime) 	85.25.152.185	
```

None of the info given out is my actual ip address

---

### Post by teddks on 2008-12-31
> **Falc7 said:**
> oops, i forgot to do that. They are disabled now, and this is the info i get 

```
Field	Data	Dependency
External Address 	85.25.152.185	Browser
Internal Host 	unknown	Java
Internal Address 	unknown	Java

DNS Server (Java) 	unknown	Java
DNS Server (HTTP) 	unknown	Browser
DNS Server (Word) 	unknown	Office
DNS Server (iTunes) 	unknown	iTunes
DNS Server (Quicktime) 	85.25.255.10	Quicktime

External NAT (Java)	unknown	Java
External NAT (Flash)	unknown	Flash
External NAT (Word)	unknown	Office
External NAT (iTunes)	unknown	iTunes
External NAT (Quicktime) 	85.25.152.185	
```

None of the info given out is my actual ip address

I'm still worried about that quicktime stuff showing up; while on my setup, I also get an External NAT with the same value as my exit node, I don't get the DNS server. But I suppose that doesn't really matter, as long as you stay safe.

While you're there, this site might be helpful:
[http://a5ec6f6zcxtudtch.onion/](http://a5ec6f6zcxtudtch.onion/)

That's a Tor-only .onion site run by the German Privacy Foundation. It's accessible over Tor and I2P as a hidden site, meaning there's end-to-end encryption on it. It has submission services for the Mixmaster anonymous email network, so you can send email anonymously without having to install the Mixmaster software. Make sure the email is encrypted with PGP/GPG -- GPG is installed by default on Ubuntu, and you can set up an encryption key pair using Seahorse (Applications>Accessories>Passwords and Encryption Keys). Your recipient will also need to have a key pair, so set that up with them before leaving.

Good luck.

---

### Post by Falc7 on 2009-01-01
Thanks very much for your help. I will give encrypted email a try soon, that quicktime info dosen't matter does it?

---

### Post by teddks on 2009-01-01
> **Falc7 said:**
> Thanks very much for your help. I will give encrypted email a try soon, that quicktime info dosen't matter does it?

Well, if you don't have that plugin installed, it doesn't. That's probably just the DNS server for your exit node, judging by the IP being in the same subnet as the exit node IP.

---

### Post by hyper_ch on 2009-01-02
tor is slow... what you could do is get a VPN access... either if you have a box at home you can start a vpn connection to it. Then the access of your computer to the computer at home is encrypted and you basically do the requests from home or you could rent a vpn account from a provider which does the same.

---

