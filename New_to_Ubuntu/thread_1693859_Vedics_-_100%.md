---
title: "Vedics - 100%"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-02-23
Hello,  I have installed Vedics.  When I click on the icon to start it , it runs at 100% of CPU. 

There is no way to stop it other than to do a restart.

How can I fix this ??

                 Thank's    COMPUTIAC  ](*,)


  In the read-me it calls for a Java run time. Is this something already in Ubuntu or do I need to install it ??  How ??

---

### Post by Perfect Storm on 2011-02-23
If you haven't already installed it by yourself, then no. Enable the partner repositories and install sun java jre, fonts, plugins.

---

### Post by COMPUTIAC on 2011-02-23
Where do I find this ??  Software center or Package manager ?

   Thank's

---

### Post by oldos2er on 2011-02-23
Run ```
software-properties-gtk
``` Under the 'Other Software' tab, tick the two boxes for the partner repository. When you're done, run ```
sudo apt-get update && sudo apt-get install sun-java6-jre
```

---

### Post by COMPUTIAC on 2011-02-23
Hello,  I am trying this for a second time, I guess I messed up the first time and stopped by mistake thinking it had crashed. 

In the terminal , it was running and a window covered it with a License agreement. No way to see what is going on and no way to agree to license.

Should I just let it run ??           It is still running now !

  Thank's  COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-23
Hello , can some one tell me how long this takes. It has been an hour and not much has changed.

    Thank's   COMPUTIAC

---

### Post by jeremyjjbrown on 2011-02-23
Make sure the core fonts or jre installer dialog box isn't hiding below one of you windows waiting for your OK to proceed.

---

### Post by COMPUTIAC on 2011-02-23
Hello, No nothing hiding.  The terminal still has the license agreement plastered across it, so I can't tell what is going on.

There is no way for me to do anything with it to see what is going on behind it.

COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-23
Hello, This is all I see.

      COMPUTIAC


Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                    
 &#9474;                                                                             
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)             
 &#9474;                                                                             
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM      
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON    
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE    
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY      
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE     
 &#9474; TERMS OF THE AGREEMENT.                                                     
 &#9474;                                                                             
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary       
 &#9474;     form, any other machine readable materials including, but not           
 &#9474;     limited to, libraries, source files, header files, and data files),     
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       

   It shows the whole agreement when I scroll down, but again there is nothing to click on.
 &#9474;

---

### Post by jeremyjjbrown on 2011-02-23
Is your machine frozen then? Are you posting on the same machine?

---

### Post by COMPUTIAC on 2011-02-23
Hello, Yes , I am posting on the same machine.  I can do everything else, this seems to be not doing anything at all !  
   
Meaning the Java deal.

  COMPUTIAC

---

### Post by jeremyjjbrown on 2011-02-23
click the left key on your keyboard.

you'll highlight the OK press enter

Agree to the terms with the arrows again and click enter.

---

### Post by COMPUTIAC on 2011-02-23
Hello, what do you mean by the left key on the keyboard ?

I can highlight it with the mouse and click on it, but this will not do anything.

  COMPUTIAC

---

### Post by jeremyjjbrown on 2011-02-23
The left arrow key. Just below enter.

---

### Post by COMPUTIAC on 2011-02-23
Hello , I played with the arrow keys and finally got through to the agreement and checked it off. (OK) . I appears to have finished installing.  

 Now I will try to run the VEDICS program , which is why I went through this in the beginning .

    Thank's for your help,

                             COMPUTIAC

---

### Post by jeremyjjbrown on 2011-02-23
maybe it's the right arrow key. That how you toggle in the terminal dialog boxes.

---

### Post by COMPUTIAC on 2011-02-23
Hello , Installing the Java fixed the problem with the CPU,  The problem now is VEDICS will not start.  Should I try to install it again , or is there a quicker fix to this ?

  COMPUTIAC

---

### Post by COMPUTIAC on 2011-02-23
> **jeremyjjbrown said:**
> maybe it's the right arrow key. That how you toggle in the terminal dialog boxes.


It was the left key I believe.  Thank's for the info. I did not know this before.


COMPUTIAC

---

### Post by jeremyjjbrown on 2011-02-23
How could you have known? Thankfully I remembered that one. Why they don't have a line explaining what to do is beyond me.

---

### Post by COMPUTIAC on 2011-02-23
Hello , Yes I know what you mean.  Any ideas on how to get VEDICS running now  ?

  COMPUTIAC

I have noticed once in a while in the terminal, it gives " suggestions " for what to try and type.

---

### Post by jeremyjjbrown on 2011-02-23
The readme in the tar should tell you were it lives in the gnome menu or what command launches it.

---

### Post by COMPUTIAC on 2011-02-23
Hello , I still can not get this thing going. I read and reread the install , and reinstalled it twice. Still nothing.

I have no idea what to do next , maybe try to remove it and start over again which doesn't make a whole lot of sense    


                                                   COMPUTIAC](*,)

---

