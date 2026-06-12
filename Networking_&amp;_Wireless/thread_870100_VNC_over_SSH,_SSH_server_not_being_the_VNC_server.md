---
title: "VNC over SSH, SSH server not being the VNC server"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by P4man on 2008-07-25
Hi, I need some help to get VNC to work over multiple NATs, so using an SSH tunnel seems the obvious solution. 

There are several howto's explaining how to setup VNC over SSH, but they all assume the SSH server is also the VNC server. In my situation, it is not.

background: my girlfriend lives (too) far away, runs Ubuntu, and has some weird internet access that involves multiple NATs (her own router gets a private 10.0.x.x IP, no ports are forwarded to it). I need to help her regularly and really want VNC or similar for this. She is not that technical, but I can make her enter commands with the help of Skype.

Now I would like *my* machine to be the SSH server that she connects to, so I can setup my firewall, port forwarding, and unlike her, I have a static IP. This part, I think I can manage (havent tried, but seems very simple).

Once the SSH tunnel is established, somehow I would need her to run a VNC server that uses it, so I can connect to it. I have no idea how to do that. Someone told me something about setting up a reverse tunnel, but thats all I know. It also shouldn't be too hard on her side, if at all possible.

Does anyone know how to do this, and care to explain it in a detailed way? I'll be forever grateful if we get this to work.

---

### Post by Endwin on 2008-07-25
She would just need to setup a reverse SSH tunnel which is a lot like a normal SSH tunnel but in reverse. To do so:

```
ssh -R 5900:localhost:5900 <USER>@<YOUR COMPUTER>
```

If she SSH to you with that you just point your VNC to localhost:5900 and connect to her.

How this works is it sets up a listening port on the machine it connects to defaulting to the looback device. You connect to that listening port and it goes all the way back.

---

### Post by P4man on 2008-07-25
Can you elaborate just a bit ? Whatever that command does, it can't connect to my machine, as my IP isn't even in there. Would she first have to set up a normal SSH tunnel, and then setup that reverse tunnel? 

Also, who's username is she to use.. is that an account on her, or my machine?

Lastly, that port 5900, am I right assuming it has nothing to do with our NATs and firewalls, once the SSH tunnel is setup ? I only need 1 port (22 by default), right ? Thing is, my ISP blocks all low ports, so I'd have to setup SSH on a high port number on my machine, and once that tunnel is created, we have our own network with all ports enabled, an no need to forward anything else, correct?

---

### Post by Endwin on 2008-07-25
Ah thought you have done SSH tunneling with VNC before. Alright lets go through the whole setup: ASSUMPTIONS: You both are running linux/UBUNTU

**YOUR SIDE**

Have an SSH server up and running. Since you said your ISP blocks incoming low ports set up your SSH server to run on a higher port say 2222. Once you have that done make a user account on your machine that she will connect to for the purposes of this we will call her user GF and your machine is COMP_ME. She will need to be able to access COMP_ME from where she is at. this involves on your end setting up the firewall to let port 2222 point to your machine so that when she tries to ssh to your public IP she can get through to your comp.

I am assuming to look at her machine you want to run a VNC server client have a VNC client installed UBUNTU comes with one installed by default.

**HER SIDE**

First make sure she has a VNC server up and running she can set one up in System->Preferences->Remote Desktop. Take note of the password she may set.

She will create a reverse SSH tunnel with you which will create a port on your side that will connect to to access her machine. The format of this is thus:

```
ssh -R <source port>:localhost:<destination port> GF@COMP_ME -p <SSH PORT>
```

The -R flag tells SSH I want to setup a reverse tunnel. <SOURCE PORT> is the port that YOU will connect to on your machine. localhost is the computer we are setting this up on, IE your machine. <destination port> is the port on HER side you want to connect to. -p tells SSH do not use the default SSH port use this one in our case 2222.

The final command will be something like this.

```
ssh -R 5900:localhost:5900 GF@COMP_ME -p 2222
```

The reason I specify 5900 as the port is this is the default port VNC uses. Once the connection is setup on your end we finish this up:

**VNC BACK IN**

On your end open up your VNC client and point the server at localhost and leave the port at 5900 you will then have access to your GF computer if she is running a vnc server. Put in the password when it promps (if you set one) and you have access.

What we did is had her ssh to you create a listening port on your comp which then lets you connect to that port it is forwarded through SSH to her machine and connects to a specified port on her end. 

Just make sure she can access your comp with SSH and you are all set.

---

### Post by P4man on 2008-07-25
Thanks a gazillion man. That seems easy enough.

I'm just confused over one thing. When you wrote:
> 
The final command will be something like this. 
```
ssh -R 5900:localhost:5900 GF@COMP_ME -p 2222
```

Should I replace localhost with my IP address ? I mean, I should use it *somehwere * :confused::lolflag:

---

### Post by Endwin on 2008-07-25
You leave localhost you replace COMP_ME with the IP she will connect to. Localhost is where the port will be set up. There is come scary chaining of this that can go on and that is what the localhost is for.

a more accurate final command would be:

```
ssh -R 5900:localhost:5900 GF@124.32.234.12 -p 2222
```

the GF@COMP_ME is the part to say ok connect to this machine IE COMP_ME with this account GF.

---

### Post by P4man on 2008-07-25
Doh, I'm stupid.. I blame alcohol lol. Thanks mate, I'll try this, and report back.

---

### Post by P4man on 2008-08-02
This seems to work. Thank a million. I have a closely related q though, a simpler one I think. If I just want shell access to her machine without using VNC, what do I or what does she do ? Does she have to setup an SSH server and use that reverse tunnel to forward those ports to my localhost so that I can SSH back in to it, or is there a simpler solution ?

---

