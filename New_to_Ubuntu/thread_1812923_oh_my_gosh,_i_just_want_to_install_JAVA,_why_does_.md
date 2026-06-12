---
title: "oh my gosh, i just want to install JAVA, why does it have to be so HARD!!!!"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by agnisflugen on 2011-07-27
[B]
[/B]

okay, so i have a  "Asus Eee PC 1215T" netbook i don't know what specs to include, so i just copied what was in the system monitor page:

ubuntu maverick 10.10, 
kernal linux 2.6.35-30 generic 
Gnome 2.230

i want to install JAVA but i don't understand the instructions on their page:

[http://www.java.com/en/download/help/linux_x64_install.xml#download](http://www.java.com/en/download/help/linux_x64_install.xml#download)

what the heck am i suppose to put for a root password? they say, "[I]**Note about root access:**  To install Java in a system-wide location such as **/usr/local**, you  must login as the root user to gain the necessary permissions. If you  do not have root access, install Java in your home directory or a  subdirectory for which you have write permissions."

[/I]but i have no idea what they're talking about. why does it have to be so difficult?!? some programs i can download from ubuntu software center, JAVA is such a common used thing i would have thought it would be in there. how am i suppose to tell what version of JAVA to download? oh i'm so very confused.....

---

### Post by wildmanne39 on 2011-07-27
Hi, open software center and install java from there, you will need to accept the agreement when asked.

---

### Post by agnisflugen on 2011-07-27
i tried that, but there isn't a java in my software :(

---

### Post by wildmanne39 on 2011-07-27
Hi, are connected to the internet? Did you see a lot of packages when you opened software center or is it empty?

---

### Post by wildmanne39 on 2011-07-27
Hi, also you could open a terminal by hitting ctrl+alt+t then paste this command in to it.
```
sudo apt-get install openjdk-6-jdk openjdk-6-jre

```
You can accept the agreement by moving the errors keys to high light ok then hit enter.

---

### Post by agnisflugen on 2011-07-27
> **wildmanne39 said:**
> Hi, are connected to the internet? Did you see a lot of packages when you opened software center or is it empty?

yeah, i have the internet up...when i type in "java" in the search field in the software center, i see other packages, such as "openJDK java 6 runtime" and "icedtea java plugin"..they have check marks next to them indicating i installed them...but there's no plain ol' java to select.

---

### Post by wildmanne39 on 2011-07-27
Hi, you do not need plain old java, but you probably can only use ice tea or the Jdk not both at the same time.

What is it that you are wanting to do but can not because of java?

---

### Post by agnisflugen on 2011-07-27
okay, i entered the command:

sudo apt-get install openjdk-6-jdk openjdk-6-jre
and i typed in y for yes...it says it will take 36 minutes to load....so we'll see what happens after that :)

---

### Post by agnisflugen on 2011-07-27
> **wildmanne39 said:**
> Hi, you do not need plain old java, but you probably can only use ice tea or the Jdk not both at the same time.

What is it that you are wanting to do but can not because of java?



i wanted to be able to print coupons from home, but i need to install a "coupon printer" first, and i also wanted to be able to play around on this website:

[http://morph.cs.st-andrews.ac.uk/Transformer/](http://morph.cs.st-andrews.ac.uk/Transformer/)

---

### Post by Lod on 2011-07-27
If you want to install the oracle java engine you have to enable certain repositories.
Take a look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) . I believe the oracle java is in the multiverse.

---

### Post by wildmanne39 on 2011-07-27
Hi, I can not find the link but I think I remember that to be able to print coupons you had to use internet explorer with wine or virtualbox because the web site required it but I am not sure of that.

Also I have no experience with wine I do run windows when I need to in virtualbox.

---

### Post by agnisflugen on 2011-07-27
> **agnisflugen said:**
> okay, i entered the command:
 
sudo apt-get install openjdk-6-jdk openjdk-6-jre
and i typed in y for yes...it says it will take 36 minutes to load....so we'll see what happens after that :)


okay, it's done, i closed all my windows and restarted my browser...click on the "verify java" button:


[http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_20&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-30-generic](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_20&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.35-30-generic)

but it still doesn't work...dang it. i checked out the repositories link: 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

and it  confused me..i'm going to have to read over it a couple times and hopefully it starts to sink in...

---

### Post by agnisflugen on 2011-07-27
> **wildmanne39 said:**
> Hi, you do not need plain old java, but you probably can only use ice tea or the Jdk not both at the same time.

What is it that you are wanting to do but can not because of java?


maybe i should try removing one of the programs? i'll try the java JDK and see what happens...

---

### Post by wildmanne39 on 2011-07-27
Hi, what does the website for the coupons tell you when you try to get on there site, and I still believe what I said in my last post it correct.

---

### Post by Lod on 2011-07-27
> **agnisflugen said:**
>  i checked out the repositories link: 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

and it  confused me..i'm going to have to read over it a couple times and hopefully it starts to sink in...
I'm not sure if it is easier, but it can be done in the terminal as well.

Open Terminal and enter:
```
sudo gedit /etc/apt/sources.list
```
Look for all entries starting starting with # deb... and remove the #
Save and close the file and then run the commands (line by line):
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-javadb sun-java6-jdk sun-java6-jre sun-java6-plugin
sudo update-java-alternatives -s java-6-sun
```

Probably you only need the sun-java6-jre and sun-java6-plugin packages.

---

### Post by agnisflugen on 2011-07-27
> **wildmanne39 said:**
> Hi, what does the website for the coupons tell you when you try to get on there site, and I still believe what I said in my last post it correct.


i'm on this website:

[http://www.redplum.com/](http://www.redplum.com/)


and it says,

" 	    Coupon Printing 	    We’re sorry, but your coupon print request could not be processed. 
       Please ensure that you have: 
       
[LIST]
[*]Activated the Java plugin in your Internet browser.
[*]Identified a physical paper printer as your "default" printer, and that the printer is turned on.
[/LIST]
   
            	          **Coupon Printer Not Installed!**

             We've noticed you don't have the Coupon Printer installed. 
       What you should know about the Coupon Printer:     
     
[LIST]
[*]The Coupon Printer does **NOT** collect any personal information
[*]The Coupon Printer contains **NO** adware, tracking software, or spyware of any kind
[/LIST]
            The Coupon Printer is an industry-standard browser plug-in  equipped with security features required by manufacturers that issue  online coupons.     
     **To Install the Coupon Printer:**

     
[LIST=1]
[*]Click the "Install Printer" button below and complete the Coupon Printer installation process.
[*]After the Coupon Printer is installed, you may be prompted by  your browser to allow an add-on to run. If you don't allow it, we won't  be able to see that you have the Coupon Printer installed.
[/LIST]
             You should only need to install the Coupon Printer once. If you encounter any problems, please read our [FAQs]("http://www.redplum.com/info/FAQ.aspx"), or contact us [EMAIL="wecare@redplum.com"]wecare@redplum.com[/EMAIL]. Happy printing!"




i'm not familiar with using wine, all i have in it's program file is notepad, so i guess i'll need to learn more about that next...

---

### Post by wildmanne39 on 2011-07-27
Hi, it would not let you install the coupon printer would it?

---

### Post by agnisflugen on 2011-07-27
> **wildmanne39 said:**
> Hi, it would not let you install the coupon printer would it?

nope. i tried taking out the #'s, but  i think you must be right about the wine thing! dang. i don't understand why it's gotta be so difficult. the java website has instructions for installation with linux, it doesn't mention needing to use IE and wine....

---

### Post by Rusty au Lait on 2011-07-27
My 2¢
agnisflugen. You do not need to install java. All you need is the java add-on for your browser. Which browser are you using?
Another thing, your printer has to be a real printer. Adobe or any other PDF printer may not work.
Ciao

---

### Post by wildmanne39 on 2011-07-27
Hi, java works with linux it is the site that requires internet explorer. You can look here for what virtualbox is and how it works.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Your system will need to have the resources to run virtualbox but someone else will have to help you with wine I never had much luck with it.

---

### Post by agnisflugen on 2011-07-27
i'm going to just give up on the coupons for now, and go back to secretly printing them from work...but the good news is after all that tinkering i was able to get the face transforming site to work, and it didn't before so i'm happy about that :) thanks to all you guys for your help :)

---

### Post by agnisflugen on 2011-07-27
> **Rusty au Lait said:**
> My 2¢
agnisflugen. You do not need to install java. All you need is the java add-on for your browser. Which browser are you using?
Another thing, your printer has to be a real printer. Adobe or any other PDF printer may not work.
Ciao


right now i'm using firefox, but sometimes when it acts up,  i use chrome...my printer is an HP photosmart....

---

### Post by wildmanne39 on 2011-07-27
Hi, your welcome! I am happy to help.

---

