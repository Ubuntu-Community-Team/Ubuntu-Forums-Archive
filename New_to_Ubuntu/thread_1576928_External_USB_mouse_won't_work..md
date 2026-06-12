---
title: "External USB mouse won't work."
date: 2010-09-18
forum: New to Ubuntu
---

### Post by Jadesocket on 2010-09-18
I am using a thinkpad t42 which has a trackpoint and a touchpad. When i started up my laptop with the mouse in, it worked fine until after i logged in. After that it just stopped. Is this a normal problem? If so what are some fixes?

---

### Post by khelben1979 on 2010-09-18
What is the exact brand and model number of the attached mouse? 

Also, have you tried to switch to a text console and switch back to the X server? From my personal experience, it gives you back control to the mouse if the mouse pointer have stopped working. Press **ctrl + alt + f1** and then press **alt + f7** if you're on a PC or add the **fn** key button if you're on a Mac.

The source of the problem in your situation can be that the X configuration have activated something which creates a problem with your USB mouse (badly configured). To solve it, it might be necessary to have a look at this X configuration file to determine if it's correctly configured.

---

### Post by Jadesocket on 2010-09-19
thanks for the reply. i tried what you suggested and in the console it gave me the message "connect-debounce failed, port 4 disabled." over and over again. It didn't do that before so i'm guessing that's the problem.

the mouse is a belkin f8e814. its a pretty old optical mouse.

---

### Post by khelben1979 on 2010-09-19
Have you tried disconnecting the mouse after you have logged in to the X server? Also, have you tried connecting to other USB ports?

---

