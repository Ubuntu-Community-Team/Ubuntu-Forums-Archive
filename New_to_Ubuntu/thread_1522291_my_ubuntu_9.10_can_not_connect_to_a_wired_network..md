---
title: "my ubuntu 9.10 can not connect to a wired network."
date: 2010-07-02
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-02
HI!
I have this ubuntu 9.10 version. I want to connect a wired network to it. So under the networkmanager I have entered the details of my ip address, subsnet mask, and the gateway under the ipv4 option (but after fillin my gateway details it automatically becomes 0.0.0.0 But my gateway is 10.10.10.1). I have left blank the ipv6 option i.e. it is setup to automatic.
And in the end nothing happens. My firefox does not connect. It simply says, "check the spelling, possibility that not connected to the internet, check your settings and etc, etc..". 

Bye the way I am absolutely new user so I need help from the scratch.
Please help me if you have understood my problem.

I have installed this ubuntu under windows 7 as an application, not directly.
Please help me if you can 'cause i wanna dump these windows...

---

### Post by Gone fishing on 2010-07-02
exactly what have you filled in?

Does it look like:

see screen shot

---

### Post by amityadav9314 on 2010-07-02
> **Gone fishing said:**
> exactly what have you filled in?

Does it look like:

see screen shot
thanks for replying.
yes it looked very much like that.
but instead of gateway 10.10.10.1, my gateway turns to be 0.0.0.0 soon after entering and hitting the apply button.

one more thing after fillin all these entries, it says that etho is active.
and on pinging by the following command--->"ping 10.10.10.1 -t -l"
it shows the rsult of pinging.

---

### Post by Gone fishing on 2010-07-02
After entering 10.10.10.1 just click in the subnet box just to check its taken the getway settings before clicking apply.

---

### Post by amityadav9314 on 2010-07-02
> **Gone fishing said:**
> After entering 10.10.10.1 just click in the subnet box just to check its taken the getway settings before clicking apply.
i did it. But no sooner after filling the entry of gateway and turning to click anywhere it automatically turned to 0.0.0.0.
I clicked to the subnet entry after filling the gateway but on clicking to the subnet, the entry og gateway turned to 0.0.0.0

please tell me what to do now?

---

### Post by Gone fishing on 2010-07-03
If network manager wont work for you you could try manually

Have a look at this:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Networking](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Networking)

This should do it obviously you will need to change 192.168.1.1 to 10.10.10.1 etc

---

### Post by amityadav9314 on 2010-07-05
hey thanks for all those replys..
i could not connect internet under ubuntu 9.10, but later then I downloaded ubuntu 10.04 and the internet has easily connected...
thank you very much once again...

---

### Post by viralmeme on 2010-07-14
> **amityadav9314 said:**
> HI!
I have this ubuntu 9.10 version. I want to connect a wired network to it. So under the networkmanager I have entered the details of my ip address, subsnet mask, and the gateway under the ipv4 option (but after fillin my gateway details it automatically becomes 0.0.0.0 But my gateway is 10.10.10.1)

Why would you even need to type in such details a standard desktop install will automatically pick up these entries from the modem. What's the name of your ISP and what make modem do you have.

> **amityadav9314 said:**
> I downloaded ubuntu 10.04 and the internet has easily connected...

What details did you fillin in to get conncted?

---

### Post by amityadav9314 on 2010-07-15
no actually i had installed ubuntu9.10 under windows 7, but it didn't detect my connection.

Later'en i installed ubuntu 10.04, and after FILLING ALL THE ENTRIES ONLY i could somehow manage to get connected.

My internet service provider is MTNL, a government telephoning company here in INDIA.

I have entries---->>>>IP addres, gateway, subnet, and dns domain..

---

### Post by viralmeme on 2010-07-15
> **amityadav9314 said:**
> My internet service provider is MTNL, a government telephoning company here in INDIA. I have entries---->>>>IP addres, gateway, subnet, and dns domain..

Under Windows what output does ipconfig /all produce ?

See here for how to open a [DOS Prompt]("http://www.windows7hacker.com/index.php/2009/08/how-to-open-dos-prompt-command-here-in-windows-7-and-more/")

---

### Post by dineshs on 2010-07-16
> (but after fillin my gateway details it automatically becomes 0.0.0.0 But my gateway is 10.10.10.1).While manually configuring IP using Network Manager you should [COLOR="Red"]hit ENTER after filling IP,Mask and Gateway[/COLOR]. You can add DNS before clicking apply

---

