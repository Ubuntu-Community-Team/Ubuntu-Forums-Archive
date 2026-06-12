---
title: "Ubuntu creating problem"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2011-01-26
i am using ubuntu 10.10 on my laptop HP-dv6 3050tx which used to run pretty well, but now suddenly my quick launcher has moved from top of screen to left side and ubuntu is performing annoyingly slow.. what could have happened and what can i do to fix it??

---

### Post by sydbat on 2011-01-26
> **viditgoyal3009 said:**
> i am using ubuntu 10.10 on my laptop HP-dv6 3050tx which used to run pretty well, but now suddenly my quick launcher has moved from top of screen to left side and ubuntu is performing annoyingly slow.. what could have happened and what can i do to fix it??Is it after doing the recent updates? If so, it could be a particular application that you run is not currently compatible and messing things up.

More info from you (like computer specs, etc) will allow us to help better.

---

### Post by viditgoyal3009 on 2011-01-27
> **sydbat said:**
> Is it after doing the recent updates? If so, it could be a particular application that you run is not currently compatible and messing things up.

More info from you (like computer specs, etc) will allow us to help better.
i didn't do any update but i installed a few softwares like ubuntu-netbook, utouch, and 1 more which i currently forgot and since then i am having these problems. But i have removed all these softwares but the problem still persists.

---

### Post by TBABill on 2011-01-27
I have never run it, but doesn't ubuntu-netbook bring Unity desktop? If so, that may be what you are seeing. Can you do a screenshot and post it so we can better see what you are seeing on the screen? And you'll probably have to run the command "top" without quotes in a terminal to see what's using up so much CPU to slow down the machine as a start to troubleshooting that issue.

---

### Post by viditgoyal3009 on 2011-01-27
here it goes...

---

### Post by arpanaut on 2011-01-27
Yes that is the desktop offered by ubuntu-netbook, and uses mutter which IS annoyingly slow.
That is one of the main reasons the Unity desktop in 11.04 has moved to compiz for composting.

At gdm/login after you select the user to login, on the bottom is an area to select a session to log into,
choose Ubuntu desktop edition and your normal session should be restored. 
That choice should persist until you change it yourself.

Hope that Helps.

---

### Post by viditgoyal3009 on 2011-01-27
> **arpanaut said:**
> Yes that is the desktop offered by ubuntu-netbook, and uses mutter which IS annoyingly slow.
That is one of the main reasons the Unity desktop in 11.04 has moved to compiz for composting.

At gdm/login after you select the user to login, on the bottom is an area to select a session to log into,
choose Ubuntu desktop edition and your normal session should be restored. 
That choice should persist until you change it yourself.

Hope that Helps.
thanks a lot... it really relieved me..

---

