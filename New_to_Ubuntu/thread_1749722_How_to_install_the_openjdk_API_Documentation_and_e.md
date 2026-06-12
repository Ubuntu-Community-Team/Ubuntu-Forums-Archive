---
title: "How to install the openjdk API Documentation and everything else?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by varunaub on 2011-05-04
I installed java using the command > sudo apt-get install openjdk-6-jdk.I want to install the API documentation.

How do I do that?

Fedora in the page [http://openjdk.java.net/install/#fedora](http://openjdk.java.net/install/#fedora) describes How to install openjdk plus using the command > su -c "yum install java-1.6.0-openjdk*"  everything including the API Documentation.In the Ubuntu section [http://openjdk.java.net/install/#ubuntu](http://openjdk.java.net/install/#ubuntu) it says how to insatll openjdk-6-jre, I changed the jre to jdk and jdk was installed But I am not able to insatll the API Documentaion.I tried using the command > sudo apt-get install openjdk-6-jdk* But the message I get is > openjdk-6-jdk is already the newest versionFrom the above scnario I am not able to conclude whether

1 Is the openjdk API Documentation installed? and if it is installed How can I find the where it is to access it  using Firefox?:confused:

---

### Post by wojox on 2011-05-04
```
file:///usr/share/doc/openjdk-6-jre/
```

---

### Post by varunaub on 2011-05-06
@[wojox]("http://ubuntuforums.org/member.php?u=802919")
         What do u mean By this 
                           >  	Code:
 	file:///usr/share/doc/openjdk-6-jre/ 

 		                   		  		  		 		 			

I am not able to find the information I want there? If it is possible Pls Guide me

---

### Post by wojox on 2011-05-06
> **varunaub said:**
> @[wojox]("http://ubuntuforums.org/member.php?u=802919")
         What do u mean By this 
                           

I am not able to find the information I want there? If it is possible Pls Guide me

Put that code in your browser.

---

### Post by varunaub on 2011-05-06
I can't find the [B]openjdk API Documentation there
[/B]

---

### Post by EagleG33k on 2011-05-06
I think this is what you want:
```

sudo apt-get install openjdk-6-doc

```

---

