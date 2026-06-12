---
title: "Ubunter 7.10 server can't connect to internet after resetting router"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by afods on 2009-07-23
Hello,

I have a Ubuntu server with about 5-6 windows xp clients. I was trying to setup a remote DVR system and was having trouble accessing the router information. For some reason it was decided to reset the linksys router so that i could access the router. Now there is no internet working, so the mail server isnt being updated and the server isn't being recongnized on the clients for file sharing. Can someone plz tell me what exactly has gone on here and where should I begin to solve this. Is the problem with the server and do i need to change settings there or is the problem with the router settings.
My other problem is that someone else set up this network a year ago and so the root password is no longer remembered or written down cuz the guy quit work. Sometimes when I try to do certain commands or make changes in files i can't cuz i'm not root. i've tried resetting the passwords and using sudo, sudo -i .... but none of them seem to work. 
I appreciate all the help, thx

---

### Post by cgb on 2009-07-23
Is the server setup to provide DHCP?  If so the router is probably also now setup as a DHCP server and this setting needs to be turned off.  If the server is not providing DHCP for the network then the problem probably lies with the router and the LAN settings since you also can no longer access the server from other computers within the network.  You need to insure the Router is set with the correct LAN IP address range and subnet mask.  You may want to determine what IP address your server is currently set for, I'm assuming it has a static address, and also locate what the IP address's of the other computers are.  You should be able to run the command "ifconfig" on the server to determine this and the windows boxes you can find this out by going to the command prompt and typing "ipconfig".  Post back with results.

---

### Post by afods on 2009-07-24
I don't know if the server is setup up for DHCP, how do I check that? I did a hard reset on the router and now I can access the web interface to make and save changes, which I couldn't do before. I can view the LAN network (i can see the other computers and access them) and ping the router, but I can't get internet access on any computer. I'm not sure what changes I have to make on the router settings for this. We don't have a static ip with our ISP. When I use ifconfig, there is eth0 and lo. The inet addr for eth0 is 192.168.2.200 (is that the static ip of the server, also what is inet addr??)

---

### Post by LookTJ on 2009-07-24
what is the output when

```
sudo route
```
is issued?

It seems to me that it's trying to get a lease from the wrong dhcp server.

---

### Post by superprash2003 on 2009-07-24
you could reset the password this way [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by afods on 2009-07-24
when using sudo route, the first time i tried it it asked for a password, but that got me no where. After that, whenever i try to use the command nothing happens.

I entered ip route instead and this is what came up:

192.168.2.0/24 dev eth0 proto kernel scope link src 192.168.2.200
169.254.0.0/16 dev eth0 scope link metric 1000 default via 192.168.2.1 dev eth0 metric 100


in the second output line "default ..." shouldn't it be going through 192.168.1.1 which is the routers ip?

Also a side note, I can only ping the router when i use my laptop and bypass the server. otherwise in general i can't even ping the router with my original setup. other computers can be pinged just not the router. there is a switch as well, does that effect anything??

---

### Post by LookTJ on 2009-07-24
So what happens when:
```
sudo dhclient eth0
```
is issued?

---

### Post by afods on 2009-07-24
sudo dhclient eth0 asks me for a password that i don't have

dhclient eth0 gets me this:

can't create /var/lib/dhcp3/dhclient.leases : permission denied
can't create var/run/dhclient.pid : permission denied
drop_privileges: could not set group id: operation not permitted

What exactly am I trying to do to get this to work? This is my first time interacting with a linux OS and I'd like to learn as much as possible. What are some of the possible issues going on here? Is the router sending out its own dhcp client and the server as well and is this causing a conflict?

---

### Post by cgb on 2009-07-24
I'm a little confused if you still are unable to access the file shares on the server or not since you said you can view the LAN network?  If the Router is at IP address 192.168.1.1 and it appears that your server is at 192.168.2.200, this would be a problem for accessing the server.  You need to set your Router back to a LAN IP address of 192.168.2.1 so that it is on the same subnet as the server.  Once this is changed it should also change all DHCP clients to the same subnet, unless DHCP is enabled on the server as well which could cause problems, as well and you should be able to see the server again.  I'm not sure how to verify if DHCP is enabled on the server since I am still new to Linux and I do not have a server setup myself.  Looks like you should be seeing some logs in /var/logs/messages referencing DHCP if it is setup.  You may want to check there.  If it is setup then you will need to disable DHCP on the router.  Also regarding the no internet access might be due to PPPoE settings previously setup in the router to provide access to your ISP that are no longer entered due to the reset.  You may want to verify with your ISP if such settings are required.

---

