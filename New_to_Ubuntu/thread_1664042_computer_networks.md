---
title: "computer networks"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-01-10
i have a small lan network of 20 computers all containing linux os majority ubuntu and some fedora...there are 20 users each user have their own id and password including me..i logged in my account here are some qyestions
1)wat command should i use in order to see which all computers in that network are alive?
2)is it possible to see which user has logged into which system?
3)suppose i dont know other's passwords ..is it possible to look into others account wen they are logged in as to wat they are doing?

i know these questions are kinda weird but they all are out of curiosity..i googed for the answers but cud not find any convincing

so pls anybody help me find the answers pls:P:P

---

### Post by endotherm on 2011-01-10
1) I would use zenmap, or an ip scanner
2) ssh into the box and see what users are associated with the TTYs. 
3) no, unless you are admin, then you may observe teh system itself including their activity. 

make sure of course, that you are authorized by your organization to perform these tasks explicitly. if you are spying on users, sooner or later a lawsuit will commence, and management seems to take notice of those for some reason.

---

### Post by vivek.pandey on 2011-01-10
> **endotherm said:**
> 1) I would use zenmap, or an ip scanner
2) ssh into the box and see what users are associated with the TTYs. 
3) no, unless you are admin, then you may observe teh system itself including their activity. 

make sure of course, that you are authorized by your organization to perform these tasks explicitly. if you are spying on users, sooner or later a lawsuit will commence, and management seems to take notice of those for some reason.

thanx for ur answer and suggestion
actually i am a second year btech student..the network am talking is a small portion of our lab and is kinda dedicated for such stuffs students are allowed to do such stuffs in that portion

 for using ssh i need to know either their ip adresses or the user name right?

---

### Post by endotherm on 2011-01-10
> **neo_aryan said:**
> 
 for using ssh i need to know either their ip adresses or the user name right?

hostname rather than username but yeah.

---

### Post by uRock on 2011-01-10
> **neo_aryan said:**
> for using ssh i need to know either their ip adresses or the user name right?
Both, the ssh command will look like ```
ssh urock@192.168.1.1
```

---

### Post by vivek.pandey on 2011-01-10
> **endotherm said:**
> hostname rather than username but yeah.

thanx once again
but as i ll enter the hostname or ip address i wud rather be asked for a password...wat wud be that?their or mine?

---

### Post by endotherm on 2011-01-10
> **neo_aryan said:**
> thanx once again
but as i ll enter the hostname or ip address i wud rather be asked for a password...wat wud be that?their or mine?

well, I will never recommend you log in as anyone but yourself (logging in as someone else's user is a big no-no), so the username would be your own. if you were to try their username, you would also need their password. 

```
ssh youruser@<hostname>
OR
ssh youruser@<ipaddress>
```

---

### Post by vivek.pandey on 2011-01-10
> **uRock said:**
> Both, the ssh command will look like ```
ssh urock@192.168.1.1
```

thanx for ur code
but suppose i wanna ssh in my friends box sitting next to me..of all ips available to me how will i recognise a particular ip belongs to a particular system?

---

### Post by endotherm on 2011-01-10
> **neo_aryan said:**
> thanx for ur code
but suppose i wanna ssh in my friends box sitting next to me..of all ips available to me how will i recognise a particular ip belongs to a particular system?

have him/her run 'ifconfig' and read the IP off to you, is the best bet. otherwise you need to know how the admins set up the lab, in terms of naming conventions and services.

---

### Post by vivek.pandey on 2011-01-10
> **endotherm said:**
> 1) I would use zenmap, or an ip scanner


well if zenmap or nmap is not installed.. is it possible to use netstat for producing same result?

---

### Post by endotherm on 2011-01-10
> **neo_aryan said:**
> well if zenmap or nmap is not installed.. is it possible to use netstat for producing same result?
nope. netstat just checks connections on your box, it does not attempt to connect to others. ZenMap/nmap actively scans the network, connecting to all other hosts it can find, and then reports back info about what boxes are out there, and what they run. this informaiton is not available on your PC so netstat can't help there.

---

### Post by uRock on 2011-01-10
Try System> Administration> Network Tools. There is a port scan tool there, but I am not sure of its quality.

---

### Post by vivek.pandey on 2011-01-11
is it anyways possible in ubuntu or in any linux to send a ping manually...?like in zenmap or nmap we ping a syatem and find whether its alive or not..can i do it by self by sending some message packets or something without using a software? pls reply:D

---

### Post by QLee on 2011-01-11
[QUOTE=neo_aryan]is it anyways possible in ubuntu or in any linux to send a ping manually...?like in zenmap or nmap we ping a syatem and find whether its alive or not..can i do it by self by sending some message packets or something without using a software? pls reply:D[/QUOTE]

Didn't they assign some books for the class you are taking? The questions you are asking sound like some that would be covered in the course work. 

Of course you can ping from a terminal window or console. The manual page for ping can be read by entering the command, man ping, in a terminal window. However, be sure this really is a lab where you are allowed to experiment, a sys admin on a real network might not appreciate your network scans and ping response might be disabled anyway.

---

### Post by vivek.pandey on 2011-01-11
> **QLee said:**
> Didn't they assign some books for the class you are taking? The questions you are asking sound like some that would be covered in the course work. 

Of course you can ping from a terminal window or console. The manual page for ping can be read by entering the command, man ping, in a terminal window. However, be sure this really is a lab where you are allowed to experiment, a sys admin on a real network might not appreciate your network scans and ping response might be disabled anyway.

its not a kinda course.so no mauals .its just for recreation and learning on your own.nobody bothers about those systems as we have another far sophisticated and a newer lab ..actually its a kinda spare lab..if we are free v can go in there and experiment ourself..the thing is we live in campus and so we are given this freedom and they are pretty sure they dont have any valuable information in that network..and i am really grateful for the concerns you are showing but there is nothing illegal or which can harm others its just i am trying to learn how administration is actually done using a linux system...

---

### Post by mikewhatever on 2011-01-11
> **neo_aryan said:**
> i have a small lan network of 20 computers all containing linux os majority ubuntu and some fedora...there are 20 users each user have their own id and password including me..i logged in my account here are some qyestions
1)wat command should i use in order to see which all computers in that network are alive?
2)is it possible to see which user has logged into which system?
**3)suppose i dont know other's passwords ..is it possible to look into others account wen they are logged in as to wat they are doing?**

i know these questions are kinda weird but they all are out of curiosity..i googed for the answers but cud not find any convincing

so pls anybody help me find the answers pls:P:P

Not only weird, you obviously try spying after the other users. Somehow, your lab story does not sound too convincing.

---

### Post by vivek.pandey on 2011-01-11
> **mikewhatever said:**
> Not only weird, you obviously try spying after the other users. Somehow, your lab story does not sound too convincing.

sir i dont know wat to say to convince you people... i can only say i cant risk my carrier to do such small things like pinging other computers..its just my curiosity to know networks and my approach using a linux box.. well if u really think i am lying which i can swear i am not you can if possible get this thread blocked..but still i wud say i am telling truth..those comps are not being used as we have recently got a new fully sophisticated with cameras all around .. but anyways i still urge if u think i am lying u can get the thread blocked...:(:(:(:(:(:(

---

### Post by mikewhatever on 2011-01-11
Let me refer you to question 3 in your list yet again. What you asked there is quite a bit more then computer pinging. The fact that you seem to deny it undermines your already transparent story even more.
As usually, the staff will decide if your requests are appropriate or not.

---

### Post by vivek.pandey on 2011-01-11
> **mikewhatever said:**
> Let me refer you to question 3 in your list yet again. What you asked there is quite a bit more then computer pinging. The fact that you seem to deny it undermines your already transparent story even more.
As usually, the staff will decide if your requests are appropriate or not.
k sir as  i dont have any option now.. i wont be posting anything more on this thread.. sorry if you thougth i was wrong in anyways but i still insist my story is real i m jsut trying to learn things ..anyways thanx for your help

---

