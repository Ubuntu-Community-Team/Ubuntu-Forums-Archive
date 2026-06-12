---
title: "Making Ubuntu a web server - IT dept wante to Try..  :)"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by chatmax on 2009-12-06
Hi ,
My name is Bill and I am an "IT guy" inside a small IT department of a small business and the owner FINALLY said NO to MS operating system charge of 700.oo for an operating system,, THATS THE GOOD NEWS,, 
The scary news in i am the guy that he has tasked to get a web server up..
I usually pop in the windows cd and go to the "install web servrces and IIS " but finally thoes days may be over if I can accomplish this,,,
 
For now this web server will just host manuals to our techs in the field,, bunch of scanned images,, so it is a very low risk task,,
 
 
I have installed Ububty server and it came up with an intimidating courser after I loged in,
I did an:
 
**sudo apt-get update **and it ran fine,, 
I can also ping google and such so I know i have good internet connectivity,,
I know all about the dyndns stuff and have several windows web servers oup now so I will understand the dns issues and all,,
 
Next I did a 
**sudo apt-get install ubuntu-desktop** and its running now,,
 
hopefully i will have a desktop when this is done,,,
 
**next steps?????????? I know I will need a web server engine... and ned to know where the web server home page is located and the port info and all.... any canned easy step by steps out there????**
 
Will a web server [ content already made ] pages that were built for Windows IIS use be able to get copied over to ubuntu ...?
 
I am finally getting off windows so i am punped !!! .. :)) 
Thanks

---

### Post by Some Penguin on 2009-12-06
[http://https://help.ubuntu.com/community/ApacheMySQLPHP]("http://https//help.ubuntu.com/community/ApacheMySQLPHP")
provides information on setting up the cliche'd LAMP stack.

[http://https://help.ubuntu.com/9.10/serverguide/C/httpd.html]("http://https//help.ubuntu.com/9.10/serverguide/C/httpd.html")
is the part of the server guide that relates directly to the Apache HTTP daemon.

---

### Post by Paqman on 2009-12-06
> **chatmax said:**
> 
[B]I know I will need a web server engine... 


If you chose to install the LAMP stack during install then you already have the Apache Web server, MySQL database, and the PHP scripting language. That should be enough to serve static and dynamic pages right there.

---

### Post by bodhi.zazen on 2009-12-06
> **Paqman said:**
> If you chose to install the LAMP stack during install then you already have the Apache Web server, MySQL database, and the PHP scripting language. That should be enough to serve static and dynamic pages right there.

In Linux managing servers is typically done either by editing text files, usually via ssh with text editors such as nano or vim or via web interfaces. 

Of the two, on a low number of servers, I prefer ssh, but once one starts managing large numbers of servers web interfaces start to look better.

My advice is that more likely then not, Linux will work just fine for your needs. The problem you will have is that my impression is that you are not overly familiar with Linux, say bash , bash commands, bash scripts, etc, so realistically be prepared to start reading. I would give yourself a realistic time frame , say 1-3 months to learn a new OS.

The links given above are good starting points and feel free to ask if you have any specific questions.

I would also suggest you start learning Apache and then mysql and php.

---

### Post by JBAlaska on 2009-12-06
Before you slit your throat after thinking about learning Apache, mysql and php lol

Check out [Webmin](http://www.webmin.com/)

[quote="Webmin homepage"]Webmin is a web-based interface for system administration for Unix. Using any modern web browser, you can setup user accounts, Apache, DNS, file sharing and much more. Webmin removes the need to manually edit Unix configuration files like /etc/passwd, and lets you manage a system from the console or remotely.[/quote]

Webmin howto for Karmic: [Here](http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/)
It should make your transition a bit less daunting.

---

### Post by chatmax on 2009-12-07
**Thanks for the advice people;;;**   ,
I did reload today, and selected the LAMP option at install time,, I also reinstalled ubuntu-desktop,,, The install said that 9.10 was avalable so I spent the day letting the box do that install..
 
Again I will NOT need to develope any content just post pages or someone elses site,, 
Will Webmin be a "quick and dirty for that""
 
Also is it fairly easy to drive ?
 
I like GUI and am not afraid to say so...  lol..
 
 
 
 
> **JBAlaska said:**
> Before you slit your throat after thinking about learning Apache, mysql and php lol
 
Check out [Webmin]("http://www.webmin.com/")
 
 
 
Webmin howto for Karmic: [Here]("http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/")
It should make your transition a bit less daunting.

---

### Post by chatmax on 2009-12-07
PS: I know you didnt take me to raise.... lol... BUT can you post an exact link to where I would go to do the install for webmin for unbuntu 9.10...
and possibly the start up command...?
 
Thaks Again...
 
 
 
> **JBAlaska said:**
> Before you slit your throat after thinking about learning Apache, mysql and php lol
 
Check out [Webmin]("http://www.webmin.com/")
 
 
 
Webmin howto for Karmic: [Here]("http://www.webxpert.ro/andrei/2009/10/29/install-webmin-on-ubuntu-server-or-desktop-9-10-karmic-koala/")
It should make your transition a bit less daunting.

---

### Post by bodhi.zazen on 2009-12-07
webmin is in the Ubuntu repos, LOL

```
sudo apt-get install webmin
```

you can alos see this : 

[http://www.webxpert.ro/andrei/2009/05/30/install-webmin-on-ubuntu-server-904-jaunty-jackalope/](http://www.webxpert.ro/andrei/2009/05/30/install-webmin-on-ubuntu-server-904-jaunty-jackalope/)

---

### Post by MadHatter21 on 2009-12-07
Webmin is great I am setting it up right now. The one thing you will have to do is give your new server a static Ip address. Does anyone know how to do this because i am doing the same thing with webmin and cannot get a static IP if my life depended on it.

Mad Hatter 21

---

### Post by chatmax on 2009-12-07
ur link shows for 9.04 ubuntu..  i am running 9.10,,, will that be ok....?
ps: will webmin give me a gui to create dif sites and such,, ??
 
 
> **bodhi.zazen said:**
> webmin is in the Ubuntu repos, LOL
 
```
sudo apt-get install webmin
```
 
you can alos see this : 
 
[http://www.webxpert.ro/andrei/2009/05/30/install-webmin-on-ubuntu-server-904-jaunty-jackalope/](http://www.webxpert.ro/andrei/2009/05/30/install-webmin-on-ubuntu-server-904-jaunty-jackalope/)

---

### Post by MadHatter21 on 2009-12-07
Just look at some screen shots of the program...

[http://images.google.com/images?q=webmin%20screenshots&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=en&tab=wi](http://images.google.com/images?q=webmin%20screenshots&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&sa=N&hl=en&tab=wi)

---

### Post by chatmax on 2009-12-09
[COLOR=Blue][COLOR=Black]I am running Ubuntu 9.10 server and the web server is running fine,, i can ping things and get to the web fine,, i did all my updates fine [/COLOR]
[COLOR=Red]BUT...[/COLOR]
sudo apt-get install webmin      
      
[/COLOR]did not work,, errors,,, 
SO I used the following:

[COLOR=Blue]sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl  [COLOR=Black] [ ran fine ] 
[/COLOR][/COLOR]
then

[COLOR=Blue]wget [http://www.webmin.com/download/deb/webmin-current.deb](http://www.webmin.com/download/deb/webmin-current.deb)
[/COLOR]
And it ran fine BUT when I try to execute a:

[COLOR=Blue]https://webbook:10000[/COLOR]

or the ip address:

[COLOR=Blue]http://192.168.0.130:10000    [COLOR=Red]they both return the same error:


Is there anything I can try from a troubleshooting perspective,,, being a newbee please keep in mind...???????????????
[/COLOR][/COLOR]------------------------------------------------------------------------------------------------
[COLOR=SeaGreen]Firefox can't establish a connection to the server at 192.168.0.130.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.[/COLOR]
-------------------------------------------------------------------------------------------------------



        
        
      


      
      






> **bodhi.zazen said:**
> webmin is in the Ubuntu repos, LOL

```
sudo apt-get install webmin
```you can alos see this : 

[http://www.webxpert.ro/andrei/2009/05/30/install-webmin-on-ubuntu-server-904-jaunty-jackalope/](http://www.webxpert.ro/andrei/2009/05/30/install-webmin-on-ubuntu-server-904-jaunty-jackalope/)

---

### Post by bodhi.zazen on 2009-12-09
After installing that .deb, run

```
sudo apt-get install -f
```

This will install any potential missed dependencies.

Then, restart apache, you are on 9.10 ?

```
sudo service apache2 restart
```

Then try connecting to the web server on port 80 (should see the default "It works").

Then, if that is working, try the webmin port again.

---

### Post by Maheriano on 2009-12-09
Going back to the beginning, a proper server shouldn't have a desktop installed on it. You should install the server edition, install Webmin and then log onto it from another secure computer on the network to administer it. Everything else is taken care of for you.

If you want to serve websites from it, create a public_html/www folder inside your /home/<username> folder and create each site in there inside a its own folder. That way you can visit each site based on its www folder.

If you're expecting this to build websites for you, it doesn't do that, it only serves them once built. If you want an easy way to make them, look into [www.wordpress.org](www.wordpress.org) and when you get good at that, check out [www.joomla.org](www.joomla.org), Open Realty and OSCommerce.

---

### Post by bodhi.zazen on 2009-12-09
> **Maheriano said:**
> Going back to the beginning, a proper server shouldn't have a desktop installed on it.

This is excellent advice, but some people feel more comfortable starting with a desktop, especially if they are new to Linux.

With time, most learn the command line.

So long as they understand the security implications, IMO, it is acceptable to start with a GUI. Again, I know, you are more often then not editing text files , and this can be done from the command line, sometimes it is nice to have some gui tools available for other things such as user management, browsing the web for solutions to problems, etc, etc.

Rather then cutting the safety cord, use this as an opportunity to learn to be comfortable with the CLI, then remove Gnome.

---

### Post by chatmax on 2009-12-09
Thanks for all the GREAT advice all, 
I do understand that I don't need a desktop when I have webmin running and also understand that webmin will not build sites,, the tip to the site that will do that is greatly appreciated also..!!

The issue is still not fixed..
I did execute the commands suggested and I can jump on this box with :

[http://webbook:80](http://webbook:80)
and it does return the index.html  "it works message" BUT still no answer from port 10000   ???

Could it be my browser settings...?  Im guessing,,,
Is there a webmin service or something that may not be running,,,?? 
It strange that I can surf and ping and get port 80 to talk as a web server but no port 10000 webmin...???  Help :)






> **bodhi.zazen said:**
> After installing that .deb, run

```
sudo apt-get install -f
```This will install any potential missed dependencies.

Then, restart apache, you are on 9.10 ?

```
sudo service apache2 restart
```Then try connecting to the web server on port 80 (should see the default "It works").

Then, if that is working, try the webmin port again.

---

### Post by bodhi.zazen on 2009-12-10
I installed webmin last night.

I used this page : [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

I added the webmin repository

deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib

Step - by - step instructions are on the page I gave you, ask if you need assistance.

I then installed it with apt-get (sudo apt-get install webmin).

Now webmin runs as root and is one of the rare times you need to set a root password (choose a strong won :twisted: )

```
sudo passwd root
```Then browse to your server:10000

you will be redirected to https

so

[https://localhost:10000]("https://localhost:100000") 

worked 

Best of luck =)

---

### Post by Maheriano on 2009-12-10
> **chatmax said:**
> Thanks for all the GREAT advice all, 
I do understand that I don't need a desktop when I have webmin running and also understand that webmin will not build sites,, the tip to the site that will do that is greatly appreciated also..!!

The issue is still not fixed..
I did execute the commands suggested and I can jump on this box with :

[http://webbook:80](http://webbook:80)
and it does return the index.html  "it works message" BUT still no answer from port 10000   ???

Could it be my browser settings...?  Im guessing,,,
Is there a webmin service or something that may not be running,,,?? 
It strange that I can surf and ping and get port 80 to talk as a web server but no port 10000 webmin...???  Help :)

It didn't work or you got an invalid certificate error? Post the error that you get here, the first time you visit Webmin it'll always throw a certificate exception and ask you if you want to add the certificate as a trusted site or not. You can't say something doesn't work if the explanation for how to get it working is right on the screen.

---

### Post by chatmax on 2009-12-27
> **bodhi.zazen said:**
> This is excellent advice, but some people feel more comfortable starting with a desktop, especially if they are new to Linux.

With time, most learn the command line.

So long as they understand the security implications, IMO, it is acceptable to start with a GUI. Again, I know, you are more often then not editing text files , and this can be done from the command line, sometimes it is nice to have some gui tools available for other things such as user management, browsing the web for solutions to problems, etc, etc.

Rather then cutting the safety cord, use this as an opportunity to learn to be comfortable with the CLI, then remove Gnome.

Sorry for the long break,,, I was side tracked with family and stuff,,,
Thanks for the advice on  SERVER ,,,
I TOOK IT,,  ))

STATUS= I am now running Ububtu 9.10 Desktop,, I have apache2 web server running and I also have webmin running LOL....!!! and it looks slick...

Before I break anything I have 1 objective......

I want to put a simple mail server on line  [ that is to say it doe NOT have to be on the internet ] it JUST has to be able to send mail to my valid work address that I have with my ISP.. ] 

My wish list is to get a old alert package that i have running on windows to send me an e-mail when a server goes down.. It os so old of a package that it has no place in it to put the password for my SMTP server on line,, So I was thinking I could send the alerts to the mail server that I bring up local,, on this box and then make a simple rule to get this mail server to send it to my pop account on the net,,
IF there is a much easier way I am all ears,, and as you see i am all for advice,,, 
Can you sugest a SIMPLE mail server that i can send and recieve mail with,, 
PS: I understand Dyndns and port forwarding on my local router ,,, so,,,  
Any my ULTIMATE goal would to have a mail server on the Web,,  ))  ...help..

PS I installed webmin the way U said and it worked straight out of the box,,
PSS: apache2 server is running also when i do a 127.0.0.1 cause when i do a sudo /etc/init.d/apache restart i get an angry message that the system cannot determine the host name and must use the localhost ip...
I CANNOT enter a static IP,,, When I try through the network connections GUI the applu button stays grey..??? 
I know, I know, Im a lost pup,, but  I will get this,,,,,, ) 
PSSS: I was a Global Director of IT for 12 years at a major Pharma and got "laid" off,, so I have to actually have to make things work again at a small IT shop and it has been a huge challenge... BUT I am much happier learning,, I never put a mail server on the web,, and may not understand how "yet" but I / We will get there... lol

Thanks Much...

---

