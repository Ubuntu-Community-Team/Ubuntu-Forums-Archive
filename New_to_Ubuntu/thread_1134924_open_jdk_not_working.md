---
title: "open jdk not working"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-24
I managed to get open jdk downloaded and installed according to the directions but so far its not working. Is there more I need to do to get it going with firefox? 

Thanks
mystmaiden

---

### Post by kpkeerthi on 2009-04-24
[This]("https://help.ubuntu.com/community/Java") might help

---

### Post by mystmaiden on 2009-04-24
I tried that before posting and got a message that jdk was the only java installed and there was nothing to configure...

---

### Post by jespdj on 2009-04-24
What do you mean with "it is not working"? If you want help, you have to be more specific. Do you get an error message? If so, then what is the error message? What makes you think that it does not work?

If you want to use OpenJDK in your browser, install the package **icedtea6-plugin**, which is a browser plug-in that uses OpenJDK Java:
```
sudo apt-get install icedtea6-plugin
```

---

### Post by mystmaiden on 2009-04-24
There was no error message, java simply didn't do anything at all on pages that have java - I got a blank box. I'll try your suggestion. Thanks much.

---

### Post by mystmaiden on 2009-04-24
I tried that but it said it couldn't find the plug-in. 

I'm pretty sure there's some obvious step I'm missing here, but I can't figure out what it is.

---

### Post by gandaran on 2009-04-24
> **mystmaiden said:**
> I tried that but it said it couldn't find the plug-in. 

I'm pretty sure there's some obvious step I'm missing here, but I can't figure out what it is.
open synaptic package manager, find the icedtea plugin, mark for install and click the apply button.
why not use sun-java instead? or are you running 64-bits ubuntu?

---

### Post by mystmaiden on 2009-04-24
when I used add/remove all available sources icedtea came up then before I could move the cursor over there to check it, it disappears. I chose jdk because its what I found on an Ubuntu page. I'm fine with sun java. Now to get rid of jdk...

---

### Post by mystmaiden on 2009-04-24
I removed open jdk, got sun java... it downloaded fine but this came up in the terminal window and it just stopped. 
Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                   

Looks like I need to accept or type okay for the permission but nothing I have done so far has worked. It's just stalled there now

---

### Post by gandaran on 2009-04-24
> **mystmaiden said:**
> I removed open jdk, got sun java... it downloaded fine but this came up in the terminal window and it just stopped. 
Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                   

Looks like I need to accept or type okay for the permission but nothing I have done so far has worked. It's just stalled there now

if you use a graphical gui, add/remove or synaptic package manager to install you wont encounter this problem.
I think you have to highlight <OK> then press enter.

---

### Post by mystmaiden on 2009-04-24
tried Synaptic first and was unsuccessful. I'm sure the problem is me not Ubuntu. 

I highlighted okay and hit enter - nothing...

found the solution on this forum, I had to hit F12 then accept the license agreement. 

Thanks all

---

