---
title: "ssh nightmare"
date: 2015-04-29
forum: Networking &amp; Wireless
---

### Post by Francis_Dunnery on 2015-04-29
I am hoping <i can find a network/ssh expert to help me figure this out. Its been 9 days now and Im still struggling to get an answer. Here is my timeline, 

Task - connect a computer in the UK to a computer in the USA via ssh in order to use the write command in terminal. 

Both my friend and I downloaded and installed ssh server
I made a user account for him on my computer using the adduser command. 
I logged into his account on my computer to test the password and username and it works locally for me. the terminal prompt now says friend@123.123.12.12 (fictional public ip) 
I found my public ip by going to whatsmyip.org
I found my personal computer ip my typing ifconfig in the terminal

I have an apple airport router. 
I logged into the apple airport utility and enabled port 22 for ssh port forwarding

so my friend should be able to type ssh friend@(my public ip) and then the connection would be forwarded to my sony laptop via the personal; ip that I set up in apple airport settings.

all we get is error, connection timed out. 

so i checked with [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and it just keeps giving the connection timed out error. 

does anyone have any ideas what i can try next?

---

### Post by Lars Noodén on 2015-04-30
> **Francis_Dunnery said:**
> Both my friend and I downloaded and ...


There's part of the problem.  OpenSSH-server is available in the Software Center or, if you prefer, via Synaptic or APT.  Try removing that which you downloaded and then install from the official repository using one of the previous methods.

Which versions of Ubuntu are you and your friend running?

---

### Post by Francis_Dunnery on 2015-04-30
i have it installed from the software center and im using ubuntu studio

---

### Post by Lars Noodén on 2015-04-30
You say you can connect locally

```

ssh friend@127.0.0.1

```

Can you also connect over the LAN via the LAN address from another machine, not the public address?

---

### Post by Francis_Dunnery on 2015-04-30
i can connect to his account via my private address inside the network. if i try to use the public ip it times out. 
ssh friend@(private ip) this works. my point is that the username and password are working right.

---

### Post by Lars Noodén on 2015-04-30
If you can connect from a second machine within the LAN then that means the problem is with the Airport router or your ISP.  Is the Airport router forwarding to the right LAN address?  If so, can you set the Airport to forward another port, a high one, to port 22 on your server and then check to see via canyouseeme.org if that port is getting through?

---

### Post by Francis_Dunnery on 2015-04-30
what i meant was that i can connect to the account i set up for my friend via terminal. friend@(my provate ip) 

im going to change the prt to 222 on the incoming. i called my local isp and they saud they didnt know if they were blocking port 22 or not so ill try 222.

---

### Post by Francis_Dunnery on 2015-04-30
ok, i had a breakthrough. i called the isp and they said that port 22 may be blocked. so i changed it to port 222 and low and behold i got a success on canyouseeme.org. the issue isnt finished but knowing the port was blocked means im not going crazy. i will keep you plugged into my situation so anyone else reading this can learn from my troubleshooting. thanks everyone

---

### Post by Francis_Dunnery on 2015-04-30
i changed the port to 222 and it worked. great stuff . my isp had blocked port 22 and my friend was typing in the wrong command on the terminal. he should have typed ssh -p 222 paulb@mypublicip
thank you for your help.

---

