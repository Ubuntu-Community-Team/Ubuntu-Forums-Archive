---
title: "Proxy Manager?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by scarmona on 2007-04-26
I've been using ubuntu at home for a while now, and recently I began using it in my office, unfortunately they use a proxy on their network, I'd like to know if there's a software that can globally manage all the proxy settings and change them with a single click (from a pop down menu from the taskbar for example) like Quickset from Dell does. It's a pain to change all the settings manually everytime i get to the office.

Any ideas?

Thanks

---

### Post by chakkaradeep on 2007-04-26
> **scarmona said:**
> I've been using ubuntu at home for a while now, and recently I began using it in my office, unfortunately they use a proxy on their network, I'd like to know if there's a software that can globally manage all the proxy settings and change them with a single click (from a pop down menu from the taskbar for example) like Quickset from Dell does. It's a pain to change all the settings manually everytime i get to the office.

Any ideas?

Thanks

afaik, you need to change in many places for each program or application you use. For example,

1) For gnome-related applications, you have to enter proxy info in **System-->Preferences-->Network Proxy**
2) Some applications require that the environment variables **http_proxy** and **ftp_proxy** are set 
3) Some applications like Synaptic(unless opened using prefixing **sudo** from terminal) doesnt take any proxy settings even if you set them in synaptic settings and will fail if you try to install/update/upgrade from **System-->Administration-->Synaptic Package Manager**. The same goes for Automatix2 too :mad:

---

### Post by scarmona on 2007-04-26
Well, that's what I've been doing so far. I was wondering if there's a one click solution or a more automated way to get it done.
But thanks for the quick reply anyways 8)

---

### Post by chakkaradeep on 2007-04-26
> **scarmona said:**
> Well, that's what I've been doing so far. I was wondering if there's a one click solution or a more automated way to get it done.


If you get to know of it, please do post it here too :) 

The problem is, each application have their own way of proxy settings and only few look into environment variables or read gconf settings and thus we will not have a single solution :(

---

### Post by sutrannu on 2007-12-07
Hey, this is Linux, right?
I have been working on this with Feisty, and now Gutsy, and it is very do-able, but it's looking like a moving target as well. I'm surprised there isn't more interest.
What I've done:
I have a script that combines all the ON and OFF commands needed for the myriad of proxy settings in Ubuntu. (Debian, Gnome, Synaptic, FoxyProxy)
The ON part
```
#. export http_proxy=http://uname:password@proxyurl.com:8080
sed -i "s/.ProxyCommand/ ProxyCommand/" /home/uname/.ssh/config
sed -i "s/foxyproxy mode=\"disabled\"/foxyproxy mode=\"patterns\"/" /home/uname/.mozilla/firefox/druidgpw.default/foxyproxy.xml
sudo sed -i "s/useProxy \"0\";/useProxy \"1\";/" /root/.synaptic/synaptic.conf
gconftool-2 -s -t bool /system/http_proxy/use_http_proxy true
```
As you can see, it's mostly brute force, replacing the switches in the config files. Unfortunately, I have mixed results. I just reinstalled Gutsy, (I was still on a beta install) and some of this broke.
1) I haven't learned enough about making the export command do that thing with the period in the front so it's commented out.
2) SSH works fine. Just commenting and uncommenting a line for the ProxyCommand. Could just as easily swap the whole file for Proxy/Non-Proxy versions.
3) I'm using the FoxyProxy extension, but you can change the firefox setting in the same way.
4) Have to us sudo to access synaptic.conf. It's working, though. (have to run synaptic at least once first to generate the file)
5) The gconftool-2 command won't take. Changing Sysy -> Pref -> Net Proxy will change the value, but not vice versa. Worked before the reinstall, though

So, you can make a script like this. If you have more apps you need to modify, it's easy enough to search through a config directory, greping for "proxy", then add a sed statement to modify the file.

The Full Script. (you will have to change things)
```
#!/bin/bash
if [ "$1" = "on" ]; then
        #. export http_proxy=http://uname:password@proxyurl.com:8080
        sed -i "s/.ProxyCommand/ ProxyCommand/" /home/uname/.ssh/config
        sed -i "s/foxyproxy mode=\"disabled\"/foxyproxy    mode=\"patterns\"/" /home/uname/.mozilla/firefox/somethingweird.default/foxyproxy.xml
        sudo sed -i "s/useProxy \"0\";/useProxy \"1\";/" /root/.synaptic/synaptic.conf
        gconftool-2 -s -t bool /system/http_proxy/use_http_proxy true
fi
if [ "$1" = "off" ]; then
        #. unset http_proxy
        sed -i "s/.ProxyCommand/#ProxyCommand/" /home/uname/.ssh/config
        sed -i "s/foxyproxy mode=\"patterns\"/foxyproxy mode=\"disabled\"/" /home/uname/.mozilla/firefox/ somethingweird .default/foxyproxy.xml
        sudo sed -i "s/useProxy \"1\";/useProxy \"0\";/" /root/.synaptic/synaptic.conf
        gconftool-2 -s -t bool /system/http_proxy/use_http_proxy false
        echo "Proxy OFF"
fi
```

I use an alias so that "p-on" will run "proxy on", and "p-off" will... well you get it. I do it like this ```
alias p-on='export http://uname:password@proxyurl.com:8080 && /home/uname/bin/proxy on'
``` to make the http_proxy bit work.

I am not an expert. A power-user? maybe. Suggestions more than welcome.

---

