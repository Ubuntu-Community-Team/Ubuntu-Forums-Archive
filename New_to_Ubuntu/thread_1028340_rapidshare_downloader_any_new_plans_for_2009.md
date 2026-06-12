---
title: "rapidshare downloader? any new plans for 2009?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by maikal_0011 on 2009-01-02
hi, i am looking for rapidshare donwloader that can wait automatically and then download the file or whateever as long as it download my all link that will be fine...



i downloaded slimt  (i can't say perfect name) and jdownloader but coudn't install it..i followed online help but all was fake or old.....


i am running ubuntu 8.10...and i am really hoping to get rapidshare downloader


please help.....(and if you any instruction where can i download them again and install them..)

thanks you for looking

---

### Post by BenAshton24 on 2009-01-02
Hey... I did a bit of googling.... Slimrat looks good... ([http://code.google.com/p/slimrat/downloads/list]("http://code.google.com/p/slimrat/downloads/list")) Just download it... extract it somewhere... install the dependencies buy running the following code in terminal...
```
sudo apt-get install libwww-mechanize-perl libgtk2-gladexml-perl
```
then just run double click on the file that is called slimrat-gui. Easy as pie XD

Hope this helps

Ben

---

### Post by ethoxyethaan on 2009-01-02
Flashgot and Downthemall work perfect for me, its been around for 6 years.

[https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/)

you can use Flashgot with Wget (it will automatically adjust cookie settings) and with Curl.

i like DownThemAll more so i use flashgot as a link to downthemall.

enjoy.

---

### Post by intense.ego on 2009-01-02
I don't think rapidshare supports pausing downloads, but for everything that does wget serves me fine.

---

### Post by maikal_0011 on 2009-01-02
thanks, man  but just quick question....

is it alwaays slow?


thanks mate

---

### Post by ethoxyethaan on 2009-01-02
Internet data is transferred at a speed of 1.046.875.263.336 Km / hour.
getting to 1.079.252.848.800 would not be worth the effort.

If you want faster Internet you will need to move to a different Universe.

---

### Post by maikal_0011 on 2009-01-03
slimrat is not doing very vell, i am connected to internet and says plugin failed 

so

how can i install and donwload jdownloader for ubuntu 8.10

---

### Post by Psyphre on 2009-01-04
Have you tried Modrapi?

I love it, its really lightweight and usefull. Its terminal based but its really really easy to use and you can stop/start downloads half way thru if you want.

[http://m0ds-ubuntu.blogspot.com/2008/01/en-rapidsharecom-download-manager-for.html](http://m0ds-ubuntu.blogspot.com/2008/01/en-rapidsharecom-download-manager-for.html)

---

### Post by jimmy the saint on 2009-01-04
Give JDownloader a shot.  It looks like exactly what you are looking for.
[http://www.jdownloader.org/](http://www.jdownloader.org/)

---

### Post by adobrakic on 2009-01-04
You don't install jdownloader. You download it from their site, and find the JDownloader.jar file that comes in the folder. Right click on it, and go to Open With -> and find Sun Java 6 Runtime

Make sure you have java installed first though.

---

### Post by leomelo on 2009-01-05
I use FreeRapid Downloader.You can download it from [http://wordrider.net/freerapid/](http://wordrider.net/freerapid/)
   It is the best Rapidshare and Megaupload downloader that i have found in the GNU/Linux world.It's free and open source.It needs Java 6.0 to start (JRE 6).(Use this command in the terminal 'sudo apt-get install sun-java6-jre'to install it.)  
   After you download FreeRapid,extract it take it to the user directory. And if you wanna make a panel launcher: right click on a panel > +Add to Panel > Custom Application Launcher > +Add > in the box called 'Name' enter FreeRapid and the box called 'Command' enter this command: 'java -jar /home/(user's directory)/FreeRapid-0.8/frd.jar

---

### Post by binbash on 2009-01-05
+1 for jdownloader

---

