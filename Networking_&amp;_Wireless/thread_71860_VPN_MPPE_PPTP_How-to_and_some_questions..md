---
title: "VPN MPPE PPTP How-to and some questions."
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by Bigglez on 2005-10-04
**What I have figured-out and what I still don't know**
*This is a composite of an older thread in the Warty section and some new material tacked-on the end. If anyone can shed some light on this stuff, that would be cool. Please check the questions at the end.*

**PART ONE**
Okay. I finally got Kubu to connect to the Internet. I am posting the steps I took here in case it help others and for myself because I can't remember all these things!
Note: I don't know if anything here is redundant or plain wrong. It works, that's the bottom line. Please correct anything, I know zip-all about networks.
First. I have done this from the Kubu 5.04 Intel LIVE CD.
I have not had a chance to test this on an installed system yet.
**Step 1: pptp-linux**
**Problem:**[I]"pptp-linux" is not available on the LIVE cd. (Well, near as damn as I could tell). I had to suck it across from a USB stick.)
Have a stiffy or a USB storage-device or another network connection available so that you can suck "pptp-linux_1.5.0-4_i386.deb" (or whatever version you have) across to the kubu machine.[/I]
I *think* that the installed version of Kubu/Ubu already install pptp-linux, so you should be good to go.
If you need to install it:
```
dpkg -i pptp-linux_1.5.0-4_i386.deb
```
**Step 2: Editing some text files**
Open a root terminal somehow. You might need to open a normal one and then type:```
sudo su
```
Create "/etc/ppp/options.pptp" 
(Sets options for all tunnels, they say.)
Put this stuff in it:```
lock
noauth
refuse-eap
refuse-chap
refuse-mschap
nobsdcomp
nodeflate
require-mppe-128
```
Create or add to "/etc/ppp/chap-secrets" 
(Holds username and password)
[i]$TUNNEL = Some name. You decide. It's used all over the place, so keep it simple. 
$USER = Your username.
$IP = The IP address of your gateway (or ISP), or whatever.
Replace them all as appropriate.[/i]
Put this info into the file:
```
$USER $TUNNEL password *
```
Where you obviously insert your info as appropriate.
Create "/etc/ppp/peers/$TUNNEL"
(Does some stuff, I dunno.)
Put this rubbish into it:
```
remotename $TUNNEL
linkname $TUNNEL
ipparam $TUNNEL
pty "pptp $IP --nolaunchpppd "
name $USER
usepeerdns
require-mppe
refuse-eap
persist
debug dump
noauth
file /etc/ppp/options.pptp
```
**Step 3: Starting the VPN connection**
Enter this command as root:
```
pon $TUNNEL
```
To diagnose problems try this:```
pon $TUNNEL debug dump logfd 2 nodetach
```
To stop the tunnel, I am informed you use:```
poff $TUNNEL
```
**Step 4: Making it "see" the Internet.**
I don't know if you will have to do this, I have to do this for my ISP situation. It makes a default route that works across the VPN tunnel. I am guessing here, but I think this moves all packets across the VPN link by telling the O/S that if it can't figure out where to send them it should just "default" to sending them to the ppp0 device. Don't quote me.
Enter this command as root:
```
ip route add default dev ppp0
```
And now you should be able to surf and so on.

----------------------------------------
**PART TWO**
I was at an Ubuntu installed machine today (as opposed to a live-cd boot like in Part One) and I tried to connect via VPN as per my prior post. It worked, but as soon as I tried to boil the process down to a single icon-click, I hit some trouble.
What I found was:
Note: We'll use the name "VPN" for the tunnel, and this is all as root.
When you run ```
pon VPN
```
It connects to the VPN, then:
```
ip route add default dev ppp0
```
Creates the route. This worked everytime.
Then, when I tried to get the **pon** thingum to create the route for me by (me) writing a script called **/etc/ppp/ip-up.local** which contains the same "ip route add...." command as before, the thing would stop working. I would get a connection, but no route.
Eventually I figured that there was a VPN connection, but that the ip-up.local script is being called **too soon** in the process. It needed a delay between stage 1 and 2.
So, I created three scripts:
ONE: Called PONVPN
```
pon VPN
```
TWO: Called ROUTEVPN
```
ip route add default dev ppp0
```
THREE: Called GO
```
cd /etc/ppp
./PONVPN
sleep 5s
./ROUTEVPN

```
Make them all executable.
So, when I run ./GO as root - it worked.
Now, as a normal user this works:
```
gnome-sudo /etc/ppp/GO
```
You can make an icon from this command in gnome or KDE.

-------------------------------------
**QUESTIONS**
Is there a better way to do this? 
I don't like hardcoding the device as "ppp0". What if the connection drops and another is made, but this time it's ppp1? Suddenly the script won't work.

Also, Is there a way to get the VPN to reconnect when it is disconnected? It would be great to be able to set a delay, say 5 minutes and then have it auto-reconnect.

**For more information go to [www.pptclient.sourceforge.net](www.pptclient.sourceforge.net)**

---

### Post by Bigglez on 2005-10-04
Oh, just to add, if you suggest **pptpconfig** - well I tried it today and the repository where it lives keeps returning Error 404's.

Why is is not in one of the common Repos, so we can all apt-get it without fussing about with obscure searches on this forum and then having to deal with 404 issues. Just wondering.

---

### Post by Bigglez on 2005-11-18
More developments.
After you have done the things (as per my OP) in /etc/ppp, add this step:
echo "ip route add default dev $1" >> /etc/ppp/ip-up.local
chmod +x /etc/ppp/ip-up.local

Now can connect with the line:
pppd call $TUNNEL
(where $TUNNEL is your VPN tunnel name as per your /etc/ppp/peers file)

THEORY:
To make the VPN reconnect on boot and on fail do this once:
echo "S1:2345:respawn:/usr/sbin/pppd call $TUNNEL nodetach" >> /etc/inittab
init q

These two things make ppptconfig redundant really. (I never had anything but hassles with it on Ubu/Kubu anyway.)

---

