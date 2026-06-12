---
title: "firefox - can somebody help ????? !!!!!!!"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by stanyo on 2008-07-30
i have ubuntu 8.04 installed on my machine. I have webbrowsers - opera 9.51, firefox 3.0.1 and firefox 2.0.0.16. 
i dont have problem to open in example: [www.academynetspace.com](www.academynetspace.com) or [www.laptop.bg](www.laptop.bg) with firefox 2.0 and opera. (btw: for firefox 2 if only firefox 3 isnt started- this is not important) 
the problem is next - with firefox 3.0 when i try to open the above sites i see big circle with play button. when i press play button he disappear and ..... nothing else happen. this button is some kind of application that i cant remove. his name is swfdec 0.6.0. i try to remove swfdec 0.6.0 , it was success. but the ******* thing is steel present in firefox 3. i try to remove firefox 3. and than install it again. the swfdec is still there. what can i do???? can somebody help please ???? 10x
:confused: i thinking for kubuntu now

---

### Post by nbayiha on 2008-07-30
Dude is really impossible to understand what is you problem :lolflag: .
From what i understand you were using swfdec plugins , and you couldn't open some windows.
So first what i will advise you to do, is to uninstall swfdec and install gnash or flash plugins and try the same web page and report here what happen.

---

### Post by stanyo on 2008-07-31
cheers for answare man, but at time when i post first message i already have installed gnash and uninstalled swfdec. (and one more thing i cant start at same time firefox 2 and firefox 3.) the first printscreens are with firefox 3. second is when i press play button.

---

### Post by nbayiha on 2008-07-31
U know that having the two Firefox open create some conflict between them ? Why not using the third one ,now that he (almost)fully compatible with what the two were doing. And much more improve than the second one. :)

I will try to show you how to use both together without having problem .

> The first thing you need to do is open up synaptic and scroll down to Firefox.  
You will see that there is a ' Firefox-2 and a Firefox-3. If they are both installed you can just change your preferred browser from 'Firefox' to 'Firefox-2'.  
You can do this by going to System>>Preferences>>Preferred Applications.  Firefox 3 now uses 'Firefox' and Firefox 2 now uses 'Firefox-2', so to web browser put custom command and input the command Firefox-2 if you want it to be the main one, otherwise don't change nothing . 

So if you have any shortcuts to Firefox, you will have to change those to 'Firefox-2' as well , if you input your Firefox-2 as the main one. 

If you end up starting Firefox 3 by accident and try to go back to Firefox-2, you will find that it will not function properly. 

The only Way I have found to fix this is to remove the hided ".Mozilla" folder in your home directory.  Once you delete this folder, all of your firefox settings and extensions will be gone , so careful 

All credit to this Method goes to Drew ([http://mybrainrunslinux.com/node/17](http://mybrainrunslinux.com/node/17)).:guitar:

PS : As for me , dude you should uninstall Firefox 2 and just use the third one. And you won't any problem. :lolflag:

---

### Post by stanyo on 2008-07-31
hm i installed firefox 2 because 3 didnt work with this sites. that wasnt a problem. i solved the problem (not in your way, but i solved it). i tried to delete .mozilla :) After that starting firefox again and again swfdec is still there. 
I solve the problem with synaptic. In add/remove .. swfdec is  unistalled. but in synaptic is still there, and i uninstall it. 
this solve the problem. !!!!!! Why theres have differing between add/remove and synaptic !!!!!!
thanks a lot and you have one beer from me :guitar:

---

