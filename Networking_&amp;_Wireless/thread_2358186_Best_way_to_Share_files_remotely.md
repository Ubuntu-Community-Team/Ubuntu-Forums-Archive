---
title: "Best way to Share files remotely"
date: 2017-04-10
forum: Networking &amp; Wireless
---

### Post by chemprof1981 on 2017-04-10
Hello All,

I have ubuntu 14.04 desktop set up as a media machine and I would like to be able to access the media directly remotely (from my inlaws or while on vacation).

I have been trying to research this myself and as I am not an expert in networking I wanted a more informed opinion.  Here is what I figured would work best:

1. get Dyndns so that I can access homenetwork.  
2. I have ssh and sftp server already running on my ubuntu machine and it is set up with a static IP address within my home network.  My router has setting to configure ddns but how do I know what port to open for sftp?  Is this the best way or is there a better way to share the files?  I want to be able to stream them over the internet to another computer.
3. Do I need to create a new user to access the files?  I only want the remote access to the media directory - no where else.

Thanks in advance for the comments and help.  I realized someone may have asked this before but I ahve been unable to find what I am looking for.

---

### Post by TheFu on 2017-04-10
ssh/sftp/scp all share the same port - which is configured in different ways.  I usually have my router do port translation from ... I don't know 63022/tcp on the router WAN port --> 22/tcp on the server.  22/tcp is the default for ssh, but it is best not to expose that to the internet.  It is also best NOT to allow passwords to authenticate for ssh - always force ssh-keys for that.  And block brute force by using denyhosts or fail2ban. To support media, this is NOT the best way, IMHO.

"Best" is highly subjective, so I'll just suggest using the Plex Server. It can stream video and audio files over an http connection, which doesn't need to be available over the internet - use a VPN or ssh tunnel to access it.

I have a little script that uses an ssh-SOCKS proxy to my home network using the chromium browser to access the Plex Server web page for remote streaming.

```
#!/bin/bash

# Only start SOCKS proxy if necessary
if  [ $(ps -eaf |grep ssh |grep -c 64000) = 0 ] ; then
   # Setup SOCKS proxy through home server
   echo "Starting ssh SOCKS Proxy"
   ssh -f -C -D 64000 mydynamic.example.com -NT 
fi 

# Star private firejail with chromium, going through 
# just setup SOCKS proxy
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:64000"; 
firejail --private chromium-browser \
         --proxy-server="socks5://localhost:64000" &
```
Clear as mud?

Then I simply point the URL in the browser for the plex server port with the normal web interface ... [http://myplex:32400/web](http://myplex:32400/web) ... this goes thru the proxy and finds the myplex on the LAN back home. Simple.  My laptop has the internal IP for myplex in the /etc/hosts file.

Done and done.  

OpenVPN using UDP would be slightly more efficient and won't leak DNS requests (though since I'm using a /etc/hosts no leaks will happen).  But openvpn is non-trivial to configure. Whereas openssh is pretty easy and useful for 50 other reasons.

#1 makes life easier. Do it.
#3 could be done, but I don't bother.

---

### Post by again? on 2017-04-11
```

```I also use plex and ssh but a bit differently than TheFu.
I didn't want to mess around with a dynamic DNS provider as I rarely connect remotely, so I have a script running which every hour 
creates a text file in my sync folder with my current IP address. (I use [**_MEGAsync_**]("https://mega.nz/") but would also work with dropbox)
```
#!/bin/bash

#	Creates a text file showing current Wan IP Address in sync folder.
#	Can then access via sync app on phone to change IP for ssh access

# kill $(ps -C get-ip-loop -o pid=)

#------------------User settings-----------------------
# path to your sync folder
syncfolder=$HOME/MEGAsync
# update interval (minutes)
updateInterval=60

#----------------End User Settings---------------------

while true; do
  filedate=$(date +%Y-%m-%d_%H:%M) # yyyy-mm-dd_hh-mm
	rm $syncfolder/myip* # removes current file just to make sure sync occurs
	curl -q icanhazip.com > $syncfolder/myip_$filedate.txt

## uncomment to also send mac address 
#	ifconfig -a | grep -Po 'HWaddr \K.*$' >> $syncfolder/myip$filedate.txt

	sleep ${updateInterval}m 	
done
exit 0
```

I can then retrieve my current IP by signing in to my mega account via the app or a browser and ssh to my home computer and start plex when needed.

I permanently disable the auto starting of plexmediaserver on my home PC with
```
sudo systemctl disable plexmediaserver
```

I can then control the server via ssh using the following commands
```
sudo systemctl stop plexmediaserver
sudo systemctl start plexmediaserver
systemctl status plexmediaserver
```


To make things easier I created bash aliases
```
alias **plexstart**='sudo systemctl start plexmediaserver'
alias **plexstop**='sudo systemctl stop plexmediaserver'
alias **plexstatus**='systemctl status plexmediaserver'

```

I mainly connect to plex from my Android phone and using
the [plex]("https://play.google.com/store/apps/details?id=com.plexapp.android&hl=en"), [megasync]("https://play.google.com/store/apps/details?id=mega.privacy.android.app&hl=en") and [juicessh]("https://play.google.com/store/apps/details?id=com.sonelli.juicessh&hl=en") apps makes it easy.
The Plex phone app also works well with a chromecast device.

---

### Post by TheFu on 2017-04-11
I love it!  

Running a nextcloud sync server here ( it does much more than that), so having a DNS provider is still required. ;)  I prefer not to place files/data on  
> "someone else&#8217;s hard drive attached to someone else&#8217;s server in someone else&#8217;s data center at the end of an Internet pipe controlled by someone else. If that works for you &#8211; and it might! &#8211; great. But do be aware of what you are doing."

That script and aliases won't work as-is on 14.04. No systemctl. Still, it is a reasonable example of how putting tiny steps together solves the issue. Nice.

---

