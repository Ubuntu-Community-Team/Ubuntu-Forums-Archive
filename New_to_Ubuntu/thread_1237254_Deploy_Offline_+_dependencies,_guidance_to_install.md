---
title: "Deploy Offline + dependencies, guidance to install"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by leulae on 2009-08-11
[FONT=Times New Roman][SIZE=3]Absolute beginner to ubuntu, I download Java ([COLOR=red]**sun-java6-jdk_6-06-0ubuntu1_i386.deb**[/COLOR]), when [COLOR=red]**deploying**[/COLOR] it ask many **[COLOR=red]dependencies[/COLOR]**. How to solve this problem with out internet connection. (Installing java [COLOR=blue]**offline**[/COLOR], get **[COLOR=blue]bundle[/COLOR]**) [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=5][COLOR=seagreen]**Or **[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]***kindly request ***[FONT=Times New Roman][COLOR=#000000][COLOR=blue]**guidance to**[/COLOR] [/COLOR][/FONT]***install [COLOR=blue][SIZE=5]any[/SIZE] [/COLOR]package offline***[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Thanks in advance [/SIZE][/FONT]

---

### Post by Rodemire on 2009-08-11
Hi, 

I would advise you change the title of your thread. The people who can help you might not pick it up if the title stay as "Dear all". 

What I can say is, unfortunately, downloading packages manually does raise problems of missing dependencies, the only way i can think of is to make sure that when you download the .deb package, you get ALL its dependencies along with the .deb. 
For your case you will have to connect to the internet again to get the required  dependencies. Sorry.
Have you read the Ubuntu pocket guide? It helps in understanding the basics, it worked wonders for me. If not follow link below:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

I hope you get the assistance you require.

---

### Post by SyL on 2009-08-11
You should not install directly a .deb file, unless this is really necessary.
For install anything, you should use the package manager GUI. 

I personally have the habit to use the command line, which has automated completion.
 So for install Java i would do the following:
```

sudo apt-get update
sudo apt-get ugrade
sudo apt-get install sun <tab> --> will show you all package starting with sun*
sudo apt-get install java <tab> --> will show you all package starting with java*

```Want further info?
Document yourself:
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)
and use google ... or cuil





HTH

---

### Post by leulae on 2009-08-11
I downloaded the book by your advise, thanks lot, only little days with ubuntu, want to Change to FOSS
  

> **Rodemire said:**
> Hi, 

I would advise you change the title of your thread. The people who can help you might not pick it up if the title stay as "Dear all". 

What I can say is, unfortunately, downloading packages manually does raise problems of missing dependencies, the only way i can think of is to make sure that when you download the .deb package, you get ALL its dependencies along with the .deb. 
For your case you will have to connect to the internet again to get the required  dependencies. Sorry.
Have you read the Ubuntu pocket guide? It helps in understanding the basics, it worked wonders for me. If not follow link below:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

I hope you get the assistance you require.

---

### Post by mac9416 on 2009-08-13
> kindly request guidance to install any package offline

The easiest way is to use [Keryx]("http://keryxproject.org/"). I'm sure you will find it very helpful.

---

### Post by EXCiD3 on 2009-08-13
+1 for keryx :D It's very simple.

---

