---
title: "Some simple Apache, php and MySQL help needed"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by garr1095 on 2010-04-16
Greetings!
 
I am a complete noob to Linux/Ubuntu, but I did read thru the pocket guide (very nice job on that BTW). So...
 
I enjoy writing php. I aksed some college friends about the best way for me to write php and not have to use a rented server and pay monthly fees just to have some fun. So one friend installs Ubuntu on an old PC I had that was collecting dust. He installed version 8.10 (I think), and I played with it for a day. I find that I really like the interface, and it boots super quick compared to my windows machine. The second day I had the machine, I wanted to start writing some code. I composed a simple test.php file and found that the php was not working. I did some research and tested apache and php. When I test apache, I got the "It works!" web page, so I assume that apache is working fine. Then I did the php test. I find that php is installed and "working" as I have php version 5.2.10-2ubuntu6.4. So I assume that php is working fine. When I write a test page, the html stuff works fine, but I dont get any php on the page. Something simple like echo 'Hello World!' does not work. All of my tests have been saved to the /var/www/ directory.
 
This Ubuntu machine will not host on the internet at all. This is simply for me to write code without the rental fees and hassle to upload files after each change for testing. Is there a specific directory I should be saving my work into so that php will work? As I sated at the start, I am a complete noob with Linux/Ubuntu.
 
Once I get php worked out, I will next need to get MySQL working with php. Once that all works I will be able to explore and learn Linux at my own pace. I need to get the php and MySQL working before I lose interest and the machine starts to collect dust again. 
 
Any advice and help is greatly appreciated!
 
Thanks,
garr1095

---

### Post by Method X on 2010-04-16
Hello.
Are you sure, that you installed php packages (php5, php5-common e.t.c)?
Make sure to do it and restart apache after that.

---

### Post by garr1095 on 2010-04-16
Awesome! Thanks a lot. Restarting Apache did the trick {kicks self in head}. Also I was browsing to the file with firefox instead of browsing to it by [http://localhost/](http://localhost/). 
 
Thanks again,
garr1095

---

### Post by garr1095 on 2010-04-16
Ok. Apache and php are working great. Now to get MySQL setup on my machine. On the server I rent there is a phpMyAdmin for MySQL. Would there besomething similar to that on my machine? I do apologize for the NOOB questions, but I also appreciate any help.
 
Thanks,
garr1095

---

### Post by garr1095 on 2010-04-16
Well I found this site:
[http://debianhelp.co.uk/phpmyadmin.htm](http://debianhelp.co.uk/phpmyadmin.htm)

When I run the install command I get this:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Apparently I am not logged in as root, but I am not sure. I am the only user on this machine. If nothing else, I am learning new things today. I hate being a NOOB tho, and having to ask simple questions like these.

Thanks,
garr1095

---

### Post by garr1095 on 2010-04-16
Ok. I read some more and found I had to run the install command with sudo. phpmyadmin is installed. Now the next steps after the install are listed as:
 
[SIZE=2]"this will install the phpmyadmin in your machine.Now if you want to access phpmyadmin you need to enter the following url in to your browser

[http://your](http://your) serverip/phpmyadmin/"[/SIZE]
[SIZE=2][/SIZE] 
Now when I point my browser to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) I get a 404 Not Found.
 
Solve one problem and another creeps into the mix.
 
Thanks for any help,
garr1095

---

### Post by dgw on 2010-04-16
You might want to take a look at this: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I've found it really helpful for installing php and MySQL. The section of that page with info on installing phpmyadmin may have a fix for your 404 problem:
> 
**If you get a 404 error upon visiting [http://localhost/phpmyadmin](http://localhost/phpmyadmin):** You will need to configure apache2.conf to work with Phpmyadmin. 

```
sudo gedit /etc/apache2/apache2.conf
```Include the following line at the bottom of the file, save and quit. 

```
Include /etc/phpmyadmin/apache.conf
```

---

### Post by garr1095 on 2010-04-16
Thank you very much for the fix and the link. I think that link will be very helpful to me. After adding the line to the apache.conf and a apache restart, I can now access MySQL with the phpmyadmin.
 
Thanks,
garr1095

---

