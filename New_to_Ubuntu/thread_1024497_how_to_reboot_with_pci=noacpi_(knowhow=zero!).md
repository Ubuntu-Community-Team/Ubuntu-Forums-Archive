---
title: "how to reboot with pci=noacpi (knowhow=zero!)"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by xenia-007 on 2008-12-29
Hi, sorry for maybe stupid question - i just have absoluteley not the smallest idea about IT..:(
have an Acer Eee PC with Ubuntu, I m not able to switch on wirless divice. When I try,  I get notice 
"wlan adapter is being enabled" , then 
"wlan ad. is being restarted" and then 
"wlan ad. failed to return. please reboot".

I opened terminal and did the "sudo lshw -C network"    - then there is some info about the wlan device (like description, physical id, bus info, logistic name etc) so i think it is recognized.

Then I did the iwconfig , and it says 
"lo & eth0   no wireless extension"

Accordimg to troubleshooting guide i should do the pci=noacpi  option, but i have absolutely no idea how to do this. I dont know how to open any other terminals or anything -> a total looser :(

Can anyone give me advice? Thank you sooo much, i m totally lost!!

xenia

---

### Post by Michael.Godawski on 2008-12-29
hey xenia-007, 

you are not a looser, you are just learning new stuff, this feeling is normal...:)

Can you please post the whole output from 
```
sudo lshw -C network
```

Also can you tell us which troubleshooting guide you follow?

Finally to add the **pci=noacpi** have a look [here]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation").

And feel free to ask whatever you like.

---

