---
title: "How do I install java?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Rigorous on 2009-05-05
I have been trying to install java by reading the instructions on their page and when i typed su into the terminal i get an error so I found out you have to use sudo apt-get install packagename, well I put the name of the file exactly and said it couldn't find package?

Thanks for the help!

Oh yes, I would also like to thank ubuntu for the free CD :)

---

### Post by aysiu on 2009-05-05
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The package you want to install is called *sun-java6-jre*

---

### Post by raymondh on 2009-05-05
Why not just use synaptic and look/search for sun-java.  I think it's sun-java6

system>administration>synaptic

Enjoy

---

### Post by Rigorous on 2009-05-05
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The package you want to install is called *sun-java6-jre*

Ok I went to add/remove and installed java... but when I go to play a java game it says I do not have java?

---

### Post by Rigorous on 2009-05-05
> **raymondhenson said:**
> Why not just use synaptic and look/search for sun-java.  I think it's sun-java6

system>administration>synaptic

Enjoy

I tried that and installed it and still when I go to play a game java is not recognized? Im using firefox and using ubuntu 8.10.

---

### Post by presence1960 on 2009-05-05
> **Rigorous said:**
> I tried that and installed it and still when I go to play a game java is not recognized? Im using firefox and using ubuntu 8.10.

Try installing this java plug in for firefox if you are using 64 bit : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

---

### Post by Rigorous on 2009-05-05
> **presence1960 said:**
> Try installing this java plug in for firefox if you are using 64 bit : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

I have 32 bit.

---

### Post by aysiu on 2009-05-05
> **Rigorous said:**
> Ok I went to add/remove and installed java... but when I go to play a java game it says I do not have java?
It may be something as simple as exiting Firefox and then starting it again.

---

### Post by raymondh on 2009-05-05
> **aysiu said:**
> It may be something as simple as exiting Firefox and then starting it again.

Aren't we able to see if java is among the plug-ins in firefox?  I think (to check) .... type in the address bar
> 
about:plugins

and then scroll if java is enabled.  If not, then java has not been installed or is improperly installed ... 

Let me see mine ...hmmmm ... yup, java enabled thru ICED TEA ... note I'm using right now a derivative of Hardy (called gOS)

Raymond

---

### Post by Sef on 2009-05-05
>  	Quote:
 	 	 		 			 				 					Originally Posted by **presence1960** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7221398#post7221398") 				
 				*Try installing this java plug in for firefox if you are using 64 bit : [http://ubuntuforums.org/showpost.php...9&postcount=59]("http://ubuntuforums.org/showpost.php?p=6791349&postcount=59")*
 			 		 	 	 
I have 32 bit.

Make sure you have the 32-bit plug in installed.  It is in add/remove too.

---

### Post by raymondh on 2009-05-05
can't seem to disable smilies...sorry

about:plugins

---

### Post by Rigorous on 2009-05-05
> **Sef said:**
> Make sure you have the 32-bit plug in installed.  It is in add/remove too.

Thank you very much!!! It works :)

---

### Post by ssdt on 2009-05-05
Download the .deb from their site and use that. That could work, I think.

---

### Post by Miljet on 2009-05-05
> Download the .deb from their site and use that. That could work, I think.

Bad idea! The instructions on the Sun site are not written for Ubuntu and are impossible for newbies to follow.

---

### Post by RealPSL on 2009-05-05
Rigorous,

If this is for your web browser (Firefox) you need to install sun-java6-plugin.

---

