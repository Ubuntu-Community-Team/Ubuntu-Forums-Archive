---
title: "(De-)Activate Proxy from Command Line"
date: 2020-10-30
forum: Networking &amp; Wireless
---

### Post by aaroncampbell2 on 2020-10-30
I want to be able to script/automate connecting to a proxy (setting up the SSH tunnel and activating it, then deactivating it when done). How can I do this from the command line?

In settings I would go to Network -> Network Proxy
[ATTACH=CONFIG]287257[/ATTACH]

Then set it to Automatic and specify the config URL (each proxy I need to connect to uses an auto-config like this, so I don't need to do all the manual settings)
[ATTACH=CONFIG]287256[/ATTACH]

How can I change that setting between Disabled and Automatic and specify the URL from the command line?

---

### Post by TheFu on 2020-10-30
I don't have the details in front of me, but I'd use the settings of the ~/.ssh/config file. Setup a different connection name for when you want the proxy.
```
host ubudesk.lan
  user thefu
  hostname regulus
  port 22 

host ubudesk.wan
  user backups443
  hostname thefu.duckdns.org
  port 49022 
```


ssh can only proxy TCP, so any UDP will "leak".

My main use for an ssh proxy is for connecting to my home LAN http/https servers over the internet. Here's the script:
$ more bin/fireproxy-home.sh 
```
#!/bin/bash

PORT=64001

# Only start SOCKS proxy if necessary
if  [ $(ps -eaf |grep ssh |grep -c $PORT ) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   ssh -f -C -D $PORT  50.12.12.34 -NT &
fi 

# Star private firejail with chromium, going through 
# just setup SOCKS proxy
sleep 3;
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:$PORT "; 
firejail --private chromium-browser \
         --proxy-server="socks5://localhost:$PORT " &
```

It has been a few months.  The new snap packaged chromium does not work with firejail. That's a separate issue.
I wanted to used firefox, but they removed the proxy option from the CLI options. A different profile is needed.

---

### Post by aaroncampbell2 on 2020-11-02
Thanks for the help! I went down that path for a while but couldn't seem to get it to process all traffic like the GUI setting does, and I was missing out on some of the handy extras the PAC file offered. I ended up finding my answer though, in `gsettings`:
```
gsettings set org.gnome.system.proxy autoconfig-url "https://your-pac-url"
gsettings set org.gnome.system.proxy mode 'auto'
```
Note: Set it to 'none' instead of 'auto' to disable it.

You can see the current settings using `get` instead of `set`:
```
gsettings get org.gnome.system.proxy autoconfig-url
gsettings get org.gnome.system.proxy mode

```
And you can see what keys are available to set for the proxy settings using:
```
gsettings list-keys org.gnome.system.proxy
```

---

### Post by TheFu on 2020-11-02
ssh cannot proxy non-TCP traffic. Beware.

---

