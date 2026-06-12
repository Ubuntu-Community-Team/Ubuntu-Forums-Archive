---
title: "SSH and dnsdyn"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by ccantaga on 2007-11-12
I am making a digital picture frame using a 20" monitor, a micro atx board, and everything I have learned from watching Norm Abrams to build a frame around it all. I have everything working on the frame side of things and am now trying to connect to the frame from another computer to make changes, and setup the slide show remotely.

I am able to use ssh to log onto the computer, but it only works if I have the IP address of the computer. I have a dynamic IP, so I need a way to figure out the IP of the picture frame to log on.

I have just signed up for an account with dnsdyn.com and installed inadyn to send the site my IP when it changes. When I try to connect to my computer using ssh, it hangs for awhile, then reports that it timed out trying to connect to port 22 at the URL I use. The syntax I use is below.

"ssh [email]username@address.homelinux.net[/email]"

I am guessing that the problems are either in how I have the server setup, or in how dyndns.com deals with redirecting ssh. I am fairly new to linux, but very very new to networking. Any help in narrowing down the problem would be very much appreciated.

Chris

---

### Post by Prefader on 2007-11-12
Make sure your router has port 22 forwarded to the ip address of the system you are trying to ssh into.  I use dyndns to make it easy to admin system at home and friends' houses, and have never had a problem using ssh.

Additionally, you really ought to set up your ssh server to use key logins, instead of password logins, if you haven't already.  Just a little bit of extra security since your server is open to the wilds of the internet.  Check the [wiki](https://help.ubuntu.com/community/SSHHowto) for instructions on setting up your keys.

---

### Post by ccantaga on 2007-11-12
Thanks for the response.

How would I go about checking to see if the router will forward port 22? I am guessing that it is forwarding the port, otherwise, I wouldn't be able to connect to the computer when I directly enter the IP address. SSH connects, I just can't seem to do it by going through dnsdyn. 

Thanks again,
Chris

---

### Post by Prefader on 2007-11-12
What happens if you ping the system?  If the dyndns account is new, it's possible that the new info hasn't had enough time to propagate.  If it responds to a ping, then the address is resolving fine, and you need to check the settings in your router.

Hmmm, is the picture frame on the same network as the system your trying to log in from?  SSH would still work then, even without port forwarding set up.

---

### Post by ccantaga on 2007-11-12
The frame isn't running right now and I am not at home. However, I did ping the site when I was at home, and it got a response. However, if I remember right, the response did not come from the same IP as the frame was running at.

Now that the frame is off, there is no response to a ping from that URL.

Not sure what that means, hopefully it sheds a bit more light on what could be setup wrong though.

---

