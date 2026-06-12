---
title: "Emerald theme not staying"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by nlsthzn on 2010-10-09
Hello,

I am using an Emerald windows border which I initialise with Alt+F2:

> emerald --replace

However once I reboot it reverts back and I have to do it again... anyway to make it stick?

---

### Post by cjv8888 on 2010-10-09
You can install the compiz fusion icon then select emerald as the Window Decorator.

---

### Post by oldos2er on 2010-10-09
You need to have compiz running as your window manager.

---

### Post by nlsthzn on 2010-10-10
> **cjv8888 said:**
> You can install the compiz fusion icon then select emerald as the Window Decorator.

> **oldos2er said:**
> You need to have compiz running as your window manager.

I am running Compiz and a custom theme that uses Emerald... and the theme works and looks great, my problem is after every reboot I have to re-run "emerald --replace"... it doesn't stay after reboot...

---

### Post by gbestrada on 2010-10-10
Here is how every time you restart your machine to keep emerald:

Go to SYSTEM->PREFERENCES->STARTUP APPLICATIONS .

click on add , and in the new box , name the application .I suggest 
name it emerald .   then type the command :   *emerald --replace *.
And click add .and you are done , the next time you reboot emerald will start from the 
beginning . 

hope it helps  :):)      :lolflag:

---

### Post by nlsthzn on 2010-10-10
> **gbestrada said:**
> Here is how every time you restart your machine to keep emerald:

Go to SYSTEM->PREFERENCES->STARTUP APPLICATIONS .

click on add , and in the new box , name the application .I suggest 
name it emerald .   then type the command :   *emerald --replace *.
And click add .and you are done , the next time you reboot emerald will start from the 
beginning . 

hope it helps  :):)      :lolflag:

Cool, will do (even though it seems unnecessarily)...

---

### Post by mcduck on 2010-10-10
There's a lot better way to do this.

You really just have to tell Compiz that you want it to use Emerald. And that's done in CompizConfig Settings Manager, go to the Window Decorations-plugin and set the "command" to "/usr/bin/emerald". That's all, Compiz now use Emerald by default. :)

Adding "emerald --replace" in Startup Applications *works*, but it's kind of backwards way of doing this. Instead of just starting Compiz with the right decorator from the beginning you'd start Compiz with GWD as decorator (as defined in Compiz options) and then immediately unload GWD and load Emerald instead. Lot of extra work for no reason.

---

### Post by nlsthzn on 2010-10-10
> **mcduck said:**
> There's a lot better way to do this.

You really just have to tell Compiz that you want it to use Emerald. And that's done in CompizConfig Settings Manager, go to the Window Decorations-plugin and set the "command" to "/usr/bin/emerald". That's all, Compiz now use Emerald by default. :)

Adding "emerald --replace" in Startup Applications *works*, but it's kind of backwards way of doing this. Instead of just starting Compiz with the right decorator from the beginning you'd start Compiz with GWD as decorator (as defined in Compiz options) and then immediately unload GWD and load Emerald instead. Lot of extra work for no reason.

Hi,

Ok, I have done it... Makes more sense this way. 


Thank you!

---

