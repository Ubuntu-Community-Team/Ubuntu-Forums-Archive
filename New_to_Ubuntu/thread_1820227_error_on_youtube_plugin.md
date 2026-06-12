---
title: "error on youtube plugin"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by eslam elbyaly on 2011-08-07
hi all , 
it the first time i open youtube , and there was a button at the top of the firefox to install missing plugins , 
i clicked on it the first time , then a window with these plugins appeared 
adobe flash player (installer),
swfdec swf player ,  
gnash swf player 
i think these are their names 
then i choosed the first to install ,

but i interrupted the installation process by cancelling it , then , when i tried to install the plugins again , an error appeared 


E: dpkg was interrupted , you must manually run 'sudo dpkg --configure
-a' to correct the problem . 
E:_cache->open() failed , please report. 

and i can not install anything of it until now , and i can not see any video on youtube 

help , please 
regards

---

### Post by haqking on 2011-08-07
> **eslam elbyaly said:**
> hi all , 
it the first time i open youtube , and there was a button at the top of the firefox to install missing plugins , 
i clicked on it the first time , then a window with these plugins appeared 
adobe flash player (installer),
swfdec swf player ,  
gnash swf player 
i think these are their names 
then i choosed the first to install ,

but i interrupted the installation process by cancelling it , then , when i tried to install the plugins again , an error appeared 


E: dpkg was interrupted , you must manually run 'sudo dpkg --configure
-a' to correct the problem . 
E:_cache->open() failed , please report. 

and i can not install anything of it until now , and i can not see any video on youtube 

help , please 
regards


just install flash-aid

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

it will install and use the most appropriate version of flash for your system.

Once installed on the right hand side of address bar click to install the configure

---

### Post by nns2006 on 2011-08-08
>  i clicked on it the first time , then a window with these plugins appeared 
adobe flash player (installer),
swfdec swf player ,  
gnash swf player 


Install these files from synaptic manager. I hope that helps.

---

### Post by lisati on 2011-08-08
> **eslam elbyaly said:**
> hi all , 
it the first time i open youtube , and there was a button at the top of the firefox to install missing plugins , 
i clicked on it the first time , then a window with these plugins appeared 
adobe flash player (installer),
swfdec swf player ,  
gnash swf player 
i think these are their names 
then i choosed the first to install ,

but i interrupted the installation process by cancelling it , then , when i tried to install the plugins again , an error appeared 


E: dpkg was interrupted , [COLOR="Red"]you must manually run 'sudo dpkg --configure
-a' to correct the problem[/COLOR] . 
E:_cache->open() failed , please report. 

and i can not install anything of it until now , and i can not see any video on youtube 

help , please 
regards
What happens when you run the following from the command line (terminal)?
```
sudo dpkg --configure -a
```

---

