---
title: "LAMP installed, where's the GUI?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by x0prah_Winfr3yx on 2008-12-16
Hello all, i'm familiar with a WAMP setup on my Vista, so please understand my frame of reference here. i'm used to having a taskbar icon that i can setup everything from, is there something of the same nature for Ubuntu?

I'm used to my sever being found at C:\wamp\www, am i to find that at var\www? and if so, how do i go about seeing my phpmyadmin? the only files i find in that folder are an index file and a testphp.php file i created.

localhost/phpmyadmin/ doesn't work (obviously)

i'm running apache2 btw.

---

### Post by x0prah_Winfr3yx on 2008-12-16
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin

solved 

found in a random forum. thanks anyhow.

---

### Post by Hospadar on 2008-12-16
Generally the default root of your webserver (At least for apache2) will be located at /var/www

There are different graphical tools you can use, but no one stop shop as far as I know.  To make your server works, apache has a default page at localhost/index.html, try pointing at it with your browser

Also the apache web administration I believe is by default at localhost:8080

As for phpmyadmin, You need to make a link from your webroot to phpmyadmin (Assuming phpmyadmin is installed correctly and you configured it for apache2 during the install)

```
sudo ln -s /usr/share/phpmyadmin phpmyadmin

``` then point yourself to
[http://localhost/phpmyadmin/main.php](http://localhost/phpmyadmin/main.php)

---

### Post by x0prah_Winfr3yx on 2008-12-16
yup, that code you included worked for me. thanks for your input on a GUI too. rather enjoying this hot cup of ubuntu

---

### Post by cariboo on 2008-12-16
There is no one gui program to administer LAMP, you've already found phpmyadmin to administer MYSQl. There is a gui tool called rapache to administer Apache. I haven't tried rapache (and don't intend to either) but it is available in the repositories. The configuration files for apaches are all text files and are located in /etc/apache2, no gui really needed.

For editing html and php I prefer Quanta, which is available in the repositories.

Jim

---

### Post by drubin on 2008-12-16
> **x0prah_Winfr3yx said:**
> Hello all, i'm familiar with a WAMP setup on my Vista, so please understand my frame of reference here. i'm used to having a taskbar icon that i can setup everything from, is there something of the same nature for Ubuntu?

I'm used to my sever being found at C:\wamp\www, am i to find that at var\www? and if so, how do i go about seeing my phpmyadmin? the only files i find in that folder are an index file and a testphp.php file i created.

localhost/phpmyadmin/ doesn't work (obviously)

i'm running apache2 btw.

If you are familiar with the start/stop GUI box here try [this]("http://webmin.com/")

---

### Post by nmvictor on 2008-12-16
I installed XAMPP for linux,I'm more comfortable calling it lampp.The terminal installatin was successfull and I even saw the terminal indicate something like

Starting XAMPP with SSL and PHP.... // this is a paraphrase of the exact Starting mySQL ...                 // statements 
XAMPP Started....e.t.c
Just when I thought I had it all,my web browser thought otherwise because pointing to [http://localhost/](http://localhost/) returned a page load error.Im so much disturbed by this as I was anxious to see XAMPP in action.Please help, could I have left something out?

---

### Post by louieb on 2008-12-16
Take a look at [Webmin]("http://www.webmin.com/")

---

### Post by Iowan on 2008-12-16
Another [WebMin]("https://help.ubuntu.com/community/WebMin") you should see.

---

### Post by drubin on 2008-12-17
> **Iowan said:**
> Another [WebMin]("https://help.ubuntu.com/community/WebMin") you should see.

Can't see how that is easier/better then the instructions on the webmin home page?

---

