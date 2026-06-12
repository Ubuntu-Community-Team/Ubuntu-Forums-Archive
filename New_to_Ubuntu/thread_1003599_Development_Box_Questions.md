---
title: "Development Box Questions"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by madhatter84gn on 2008-12-06
I am somewhat new to Linux. I have been playing around with distros for the past 5 years but never fully committed to a switch until recently. I work at an all MS shop and want to transition my personal machines over to Ubuntu. I am looking for a how-to or information on the best route to setting up development box. I will be using a new Thinkpad T500 and I know I will be doing .NET so MonoDevelopment will be needed. Is it better to do a LAMP server setup and then add the GUI or is it better to do a desktop install and then add the necessary development tools? I have found a few but not many step-by-step guides to setting up the ideal beginner development box. Any pointers in the right direction would be greatly appreciated. I still classify myself as a beginner so the easier the better

---

### Post by lovelyvik293 on 2008-12-06
First of all the ubuntu is perfect for the development.But for the Mono project you never have to use the LAMP server,the lamp is combination of linux,apache,mysql and the php(or python/perl).It's not related to the .NET.

---

### Post by madhatter84gn on 2008-12-06
I gathered that much from some of my readings, but I will be doing some web development and I know I will be interacting with databases and having to test web sites so I thought I needed the Apache and MYSQL and read somewhere it was easier to install the server image to get everything working correctly out of the box.

---

### Post by lovelyvik293 on 2008-12-06
you can install the apache and the mysql with the synaptic manager of ubuntu or if you want to use the LAMP stack then go and install the LAMPP from the [http://www.apachefriends.org](http://www.apachefriends.org)

And use of the GUI is handy and even with the GUI you have to use certain amount of commands and one more thing if you want to use the box for web development then it's good to use the desktop edition it works awesome.:p

---

### Post by directhex on 2008-12-06
Adding things later isn't hard. Don't worry about starting with a desktop.

"XSP" is the standalone "test" ASP.NET server for Mono. mono-xsp2 package.

To use it within Apache (recommended for 'serious' use, you need the mono-apache-server2 package, and the libapache2-mod-mono package (though configuring mod_mono can be a little... tricky).

If you want to use MySQL in your webapps, you want libmysql5.0-cil - but feel free to use a different DB provider

---

