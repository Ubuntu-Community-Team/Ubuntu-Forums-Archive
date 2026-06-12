---
title: "(Only for expersts) Why dont they fix this in ubuntu already"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Super D on 2008-03-21
Hello Everyone,

I'll just cut to the chase. 

I work for a  large government organization (somewhere in the middle east).  I'm not allowed to say what kind of money goes to Microsoft every year. I've been trying for years to to convince them with Linux , they say it was to hard for the employees. Thats  until  Ubuntu showed up. I've managed to work out most of the stuff. Although I've been working on Microsoft stuff for. Well  since DOS 5.(something) .. 

I have a problem with networking specially when all we have is Microsoft stuff. 

My question is: 
I have the ol' ISA authentication 404 thing with synaptic.

1- We have at least 300 PC in head quarters in HQ and 13 branches around. So I cant do all the work  on my own , not mention the hassle with personnel on getting Linux experts. (cuz they don't believe in it YET!). And seriously , I got a personal life to attend to.
2 – Most the guys I work with are basic retards , you can barely get them to go around the GUI , let alone shell commands)
3 - The guy responsible for network security has paranoia.

I want something easy , friendly and fast. I think thats what Ubuntu is about .

---

### Post by koenn on 2008-03-21
> **Super D said:**
> 
I want something easy , friendly and fast. I think thats what Ubuntu is about .
> Why dont they fix this in ubuntu already
friendly, indeed
although when it comes to fixing ICT problems, "I want it fast' is usually the wrong approach.

> ol' ISA authentication 404 thing with synaptic.
is not much to go by as a diagnosis. 
If it's simply a matter of proxy authentication, there are some threads around here that deal with that. 
Otherwise you're gonna have to be a lot more specific if you want "expert" help.

---

### Post by Super D on 2008-03-21
I'll be more specific .you put proxy adress and authorication in the Synaptic. 

> 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/adns/libadns1_1.4-0.1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/adns/libadns1_1.4-0.1build1_i386.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )


just search for " ISA proxy update " 

I've seen many threads here ( the ones that suggest NTLMAPS , and the ones that use apt.conf editing , and others ) 

I have to say two thing: 

1- they didnt work.
2- Its basic configuration. if if they work the tech-support shouldnt deal with that. 


My question is: ISA is popular, even if we denied it , its used in many windows server environments.  Why isnt it taken into consideration ? 
its one of the basics to make the updates and program sources tolls running in many invironments.  

> 
although when it comes to fixing ICT problems, "I want it fast' is usually the wrong approach


I was talking about fast in  regards toapplying the solution , not in finding a solution. I know it takes time and alot of effort.

---

### Post by Mithrilhall on 2008-03-21
I could be way off target here but couldn't you just create a local repository that all your PCs hit? If so, there should be a ton of information on the internet detailing how to do that.

[http://ubuntuforums.org/showthread.php?t=538584](http://ubuntuforums.org/showthread.php?t=538584)

---

### Post by koenn on 2008-03-21
> **Mithrilhall said:**
> I could be way off target here but couldn't you just create a local repository that all your PCs hit? If so, there should be a ton of information on the internet detailing how to do that.

[http://ubuntuforums.org/showthread.php?t=538584](http://ubuntuforums.org/showthread.php?t=538584)

To manage updates for 300 PC's, a local repository  (partial repo, apt-proxy, ... ) would indeed be the way to go.
Still, that repo server and the user managing it still need authorisation to pass through the firewall. Although that might be easier to handle than a few hundred PC's

---

### Post by koenn on 2008-03-21
> **Super D said:**
> 
My question is: ISA is popular, even if we denied it , its used in many windows server environments.  Why isnt it taken into consideration ? 
 
You've answered your own question : it's popular *in many windows server environments* - probably because ISA integrates nicely with AD, and because outfits that standardise on Windows Server tend to get *all* of their infrastructure from Microsoft. 
That said, I don't know if it's really that popular. Most places I know of, tend to opt for   firewall appliances.

> **Super D said:**
> I'll be more specific .you put proxy adress and authorication in the Synaptic. 
 
Since  passing  a username/password doesn't work (unless you've made a syntax error while editing a conf file) : do you now which authentication types that specific ISA is configured to use ? I vaguely remember that ISA offers a choice of authentication methods, from basic to fully AD integrated. Obviously, passing a username and password is no going to work if the ISA only accepts kerberos tickets.

From what I see on its website, NTLMAPS can be configured for a number of authentication methods as well, some if which - if done right - could be made to function as workarounds for (some ? 3 out of 4 ?) ISA authentication schemes.
In that case, simply copying a recipy of a forum can't be expected to work.
But again, you probably need to know what authentication your ISA is using

Also keep in mind that most of NTLMAPS is reverse-engineerde because it needs to work with Microsoft proprietary protocols that are not piblically documented. 
If that's a problem, you should speak to Microsoft and ask them how to authenticate against their ISA from a non-Windows system. 
 
But I'm not an expert, so maybe I should just lay low and see what happens in this thread.

---

### Post by Junglizer on 2008-03-21
I'm also going to mention that its hard to be a good Network Security Anaylst without some degree of paranoia.

---

### Post by Super D on 2008-03-23
Hello Guys, 

note on the side
> 

I think you got me all wrong here. 

you see , we are not comparing to Microsoft products. (we are way beyond that , now), Trust me I've been around Microsoft long enough to know that they are not going anywhere. 

The thing I wanted to emphasize is that Ubuntu is a foundation for a new generation of  userfriendly os. And unlike other systems (MAC , and Microsoft) that limit it users to its products , Linux stretches out. 


Mithrilhall , 
thanks for the tip. The Tech support have that thing going already with windows computers (the lazy bums just ask you to reboot, they dont even get off their seats , but tech support have always been like that , haah)

but still we have have some other branches that would be at least 800 KM - 1200 KM far away. and  its ahassel to tell the teams over there to do this and that. 

koenn 

the thing is ISA is not the best in the market , but its easy , even a 9 year old can operate it. thats why its uesed alot in these parts. And Microsoft marketing people make sure that it sells. 

For me I really dont like it , and it needs alot of plugins to work good. Plus, sometimes it behaves on its own and block this and that . but thats Microsoft , they dont know better. 

and when I told the security guy about NTLMAPS , he almost threw a fit. seriously. he pulled two cans of pesticide he was keeping in his drawer and started rampaging. I hate that guy. I think something is wrong with him.

---

### Post by Super D on 2008-03-23
I have a suggestions. 

If its possible someone contact the people responsible for developing the synaptic pacage manager and tell them to take this issue into consideration. 

I know its not easy to fix it. But we love you guys and hope that wish come true.. 

thank you

---

### Post by koenn on 2008-03-23
> **Super D said:**
> 
note on the side

I think you got me all wrong here.

you see , we are not comparing to Microsoft products. (we are way beyond that , now), Trust me I've been around Microsoft long enough to know that they are not going anywhere.

The thing I wanted to emphasize is that Ubuntu is a foundation for a new generation of userfriendly os. And unlike other systems (MAC , and Microsoft) that limit it users to its products , Linux stretches out.

OK, but your thread title of "fix this in Ubuntu already", the tone of tour posts ("why didn't the synaptic devs made sure their update mechanism works in any and all environments without any hassle ?"), while your real problem is 
a/ Microsoft's lack of inter-operability and 
b/ the fact that you want to pull of a migration without the cooperation of the IT department of where you work
is a bit hard to swallow.

---

### Post by koenn on 2008-03-23
> If its possible someone contact the people responsible for developing the synaptic pacage manager and tell them to take this issue into consideration.
[https://launchpad.net/synaptic](https://launchpad.net/synaptic)
[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Although I'm not sure how willing/capable devs will be to create a workaround for a problem that's caused by a proprietary firewall application with  a built-in lack of inter-operability.

Besides that, re. your OP, you're going to need to know what authentication scheme that ISA uses if you want to solve your updates problem.

---

### Post by Super D on 2008-03-23
> OK, but your thread title of "fix this in Ubuntu already", the tone of tour posts ("why didn't the synaptic devs made sure their update mechanism works in any and all environments without any hassle ?"), while your real problem is 
a/ Microsoft's lack of inter-operability and 
b/ the fact that you want to pull of a migration without the cooperation of the IT department of where you work
is a bit hard to swallow. 

> Although I'm not sure how willing/capable devs will be to create a workaround for a problem that's caused by a proprietary firewall application with a built-in lack of inter-operability.

Besides that, re. your OP, you're going to need to know what authentication scheme that ISA uses if you want to solve your updates problem. 

Man, why do you have to take it on me. I never insulted you, or been rude to you.

Please stick to the subject. the matter is not me or my reform battle I'm waging alone in currupt and ignorant organization. 

Ubuntu is a philosophy that suggest people be good to each other and help each other.

so either help me or at least be kind.

---

### Post by Super D on 2008-03-23
I think Ububntu is not ment for office work. 

I think its made for home PCs and schools. probably.

---

### Post by koenn on 2008-03-23
> **Super D said:**
> 
Man, why do you have to take it on me. I never insulted you, or been rude to you.
...
so either help me or at least be kind.
I don't know that I'm taking anything to anyone - just kindly voicing an opinion and giving some helpful pointers. Sorry 'bout that.

---

### Post by Super D on 2008-03-23
Its alright man. we're all brothers here. 

I'm just trying my best to promote Ubuntu here.

its more than  system for me you know. Its like hope to fix things.

---

### Post by david_lynch on 2008-07-21
> **Super D said:**
> I think Ububntu is not ment for office work. 

I think its made for home PCs and schools. probably.
Eh? I'm using hardy heron on my desktop here in the office where I work as a sys admin. pretty smooth sailing... but then again, we're using firewall/proxy appliances, not microsoft proxy.
:)

---

