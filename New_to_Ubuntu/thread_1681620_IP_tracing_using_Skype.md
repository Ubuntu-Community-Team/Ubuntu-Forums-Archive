---
title: "IP tracing using Skype"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by suomalainen on 2011-02-04
Ubunters,

In Windows you can use <netstat -n> to determine the IP of a person during a Skype chat.

But how does this work for Linux Ubuntu. Is there a terminal command for that?

Can looking at a previous Skype chat yield the same result?

Thank you!

---

### Post by TechWiz2100 on 2011-02-04
Just curious, but have you ever tried using netstat on a Linux machine?

If not, yes netstat works on Linux lol

Theres always Wireshark as well

---

### Post by suomalainen on 2011-02-04
TechWiz2100,

I didn't try netstat in terminal but will as soon as I get the chance. BUT do you really need to type in terminal netstat -n or not????

Also, when you are in Skype, would you or anyone else happen to know how accurate the "local time" is in the Skype profile of the person you have as a contact? I attached a pic for reference.

Thanks for your feedback.

---

### Post by TechWiz2100 on 2011-02-04
> **suomalainen said:**
> TechWiz2100,

I didn't try netstat in terminal but will as soon as I get the chance. BUT do you really need to type in terminal netstat -n or not????

Also, when you are in Skype, would you or anyone else happen to know how accurate the "local time" is in the Skype profile of the person you have as a contact? I attached a pic for reference.

Thanks for your feedback.

Lol you're starting to sound like a noob stalker

netstat should work jus fine for live captures and I believe netstat -n is for past connections? Also you may want to pipe netstat thru grep or to a file since it tends to toss out a mess of crap.

Anyway, if you don't wanna use netstat just use wireshark which has a GUI. Will probably be overkill for your purposes, whatever they may be :p

---

### Post by suomalainen on 2011-02-04
TechWiz2100,

I want to match the IP location to the Skype time location and see if they match.

Kinda like called i.d.....

Thanks for the support!

---

### Post by The Cog on 2011-02-04
> **TechWiz2100 said:**
> netstat should work jus fine for live captures and I believe netstat -n is for past connections? 

Anyway, if you don't wanna use netstat just use wireshark which has a GUI. Will probably be overkill for your purposes, whatever they may be :p
The -n means numbers - don't lookuop addresses and ports into names.

You may also like etherape which is interesting to watch and not as heavy going as wireshark.

---

### Post by suomalainen on 2011-02-04
The Cog,

Thank you for the added input. I guess what would work best for me is a client I can use during a Skype chat session which would tell me the IP of the user I'm having a chat with.

As is my understanding this can only be determined while, for example, sharing a file.

Let me know if you need more info.

Thanks!

---

### Post by suomalainen on 2011-02-05
All,

Just installed WIRESHARK but it keeps crashing on me. I'm able to open the program and capture interfaces. but when I hit start... crash...boom...bang...

Thanks for your support.

---

### Post by The Cog on 2011-02-05
I don't know what your problem is with wireshark I'm afraid. It's always been reliable for me. But try etherape - that should show you whta you want to know. Or for command line, try iftop.

---

### Post by TechWiz2100 on 2011-02-05
where did you get Wireshark from? Ubuntu software center or Wireshark website's tar/sources.

It could be that you don't have required dependencies for capture.

---

### Post by suomalainen on 2011-02-05
Wireshark seems to be working now.. I'll give it a while to see how it goes....

I was recently told that:

"I think all you need to do is run 'netstat -ptun | grep skype' when the file transfer is in process. You'll get the output related to skype with the remote IP showing. Then look up its geolocation."

So I'll try this as well. I tested it in terminal but got a root complaint. See pic.

Thanks again for the support!

---

### Post by TechWiz2100 on 2011-02-07
> **suomalainen said:**
> Wireshark seems to be working now.. I'll give it a while to see how it goes....

I was recently told that:

"I think all you need to do is run 'netstat -ptun | grep skype' when the file transfer is in process. You'll get the output related to skype with the remote IP showing. Then look up its geolocation."

So I'll try this as well. I tested it in terminal but got a root complaint. See pic.

Thanks again for the support!

lol I like how you blurred your computer name but not your (or your friend's for that matter) IP address

Anywho, netstat is giving messages because it only allows the user running the command to view their own network traffic for security reasons. sudo netstat -ptun | grep skype should remove the message but still return the same results since skype is under your userspace not root's

---

### Post by mikewhatever on 2011-02-07
A lot of people seem to be uncomfortable showing their usernames. What's the big secret?

---

### Post by TechWiz2100 on 2011-02-08
> **mikewhatever said:**
> A lot of people seem to be uncomfortable showing their usernames. What's the big secret?

I have no clue but if its for "security purposes" he already failed by showing his IP lol

Maybe his username is something rather embarrassing? :lolflag:

---

### Post by VBprogramming on 2011-12-07
It seems you cant ;)

---

### Post by josephmills on 2011-12-07
Here you go 

```

'watch --interval=2 "sudo netstat -apn -l -A inet"'

```
```

'watch --interval=2 "sudo netstat -anp --inet --inet6"'

```
```

'sudo lsof -i'

```
```

'watch --interval=2 "sudo netstat -p -e --inet --numeric-hosts"'

```
```

'watch --interval=2 "sudo netstat -tulpan"'

```
```

'sudo netstat -tulpan'


```



Hope that this helps in some way :>)


(you could always nmap that...)

---

### Post by VBprogramming on 2011-12-08
You cant!!!!!

---

