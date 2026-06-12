---
title: "[SOLVED] Default User"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by AvocadoNia on 2008-12-14
How do I make a user the default user so that when the system boots it goes directly to that user?

Thank you.

---

### Post by CatKiller on 2008-12-14
System -> Administration -> Login Window -> Security

Enable Automatic Login.

---

### Post by dwasifar on 2008-12-14
System>Administration>Login Window, click the Security tab, check the Enable Automatic Login box, and select the desired used to automatically log-in.

---

### Post by AvocadoNia on 2008-12-14
> **CatKiller said:**
> System -> Administration -> Login Window -> Security

Enable Automatic Login.
Thank you.
System>Administration....Login Window is not a choice in the next menu...

Humm...any other ideas? (I am now looking at each item of the menu to see if any have the "Security" tab/choice mentioned.

Thank you.

---

### Post by dwasifar on 2008-12-14
You can also reach the same window by typing in a terminal window:  

```
gksu /usr/sbin/gdmsetup
```

---

### Post by Sef on 2008-12-14
>  	Quote:
 	 	 		 			 				 					Originally Posted by **CatKiller** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6370333#post6370333") 				
 				[I]System -> Administration -> Login Window -> Security

Enable Automatic Login.[/I]
 			 		 	 	 
Thank you.
System>Administration....Login Window is not a choice in the next menu...

Humm...any other ideas? (I am now looking at each item of the menu to see if any have the "Security" tab/choice mentioned.

Thank you. 	

That is correct.   What's between 'Language Support' and 'Network Tools'?

---

### Post by sisco311 on 2008-12-14
> **AvocadoNia said:**
> Thank you.
System>Administration....Login Window is not a choice in the next menu...

Humm...any other ideas? (I am now looking at each item of the menu to see if any have the "Security" tab/choice mentioned.

Thank you.

Press Alt+F2 and type:
```
gksu gdmsetup
```

---

### Post by AvocadoNia on 2008-12-16
Thank you. Pardon the delayed response. The library closed and I had to leave. On Mondays the library is closed. So here I am on Tuesday...

I am using Interepid Ibex 8.10. On the menu that you reference there is NOTHING between Language Support and Language Tools.

I did successfully change the default user, thank you for the alternate route. It worked like a charm.

---

### Post by AvocadoNia on 2008-12-16
> **sisco311 said:**
> Press Alt+F2 and type:
```
gksu gdmsetup
```
Thank you. I tried this:
gksu /usr/sbin/gdmsetup

once I was out of the library and back at home, away from internet but with print out of the instructions.

The above code is what I used and it worked well for me. Thank you for also responding. My apologies for not awknowledging your response earlier. I am just getting back on to internet.

---

### Post by doobiest on 2008-12-16
I prefer the hands on approach

sudo gedit /etc/gdm/gdm.conf

Uncomment these lines and set them appropriately

AutomaticLoginEnable=true
AutomaticLogin=doobiest

---

### Post by oldos2er on 2008-12-16
> **doobiest said:**
> I prefer the hands on approach

sudo gedit /etc/gdm/gdm.conf

Uncomment these lines and set them appropriately

AutomaticLoginEnable=true
AutomaticLogin=doobiest

 When calling a graphical program such as gedit, use "gksu" in place of "sudo".

---

### Post by doobiest on 2008-12-16
Why, the results are the same. sudo gedit works.

Anyway I dont use gedit i'd use vi, im just sayin

---

### Post by drs305 on 2008-12-16
> **doobiest said:**
> Why, the results are the same. sudo gedit works.

Anyway I dont use gedit i'd use vi, im just sayin

Here's a good explanation:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

