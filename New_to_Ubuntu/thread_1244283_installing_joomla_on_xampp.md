---
title: "installing joomla on xampp?"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Kezz Kezz on 2009-08-19
I'm trying to set up joomla and then virtuemart so I can learn how to use it on my pc before I put it on the net. I've managed to install xampp and phpmyadmin and I've created a new database for it. I'm following a book that's aimed at windows so I'm not getting anywhere fast.

I've changed the permissions for /var and created a new folder /var/www/shop The book says to extract joomla somewhere then copy the installation files to /shop. Then going to localhost/shop should bring up the joomla installation pages, but it's bringing up "Index of /shop" and a list of what's in there....

What am I doing wrong? Are the instructions in this book completely useless for ubuntu? 

If anyone can help can they do so step by step? I'm a linux newbie. 

:confused:

---

### Post by mangurt on 2009-08-19
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

Here's a pretty good guide.

---

### Post by Kezz Kezz on 2009-08-21
thanks, is there not a way of doing it without the terminal then?

Using that guide I got to > Set a mysql-root password (not the same as a root password, but a password for mysql) and got this message:

> kerri@kerri-desktop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


What did I do wrong :confused:

---

### Post by Kezz Kezz on 2009-08-21
Also I can now go to localhost/joomla and I do get the first installation page up, but above that are these errors: 
> 
**Warning**:  session_start() [[function.session-start]("http://localhost/joomla/installation/function.session-start")]: open(/var/lib/php5/sess_5d32ebe6212cf215f24439ce509d42b7, O_RDWR) failed: Permission denied (13) in **/var/www/joomla/libraries/joomla/session/session.php** on line **423**

**Warning**:  session_start() [[function.session-start]("http://localhost/joomla/installation/function.session-start")]: Cannot send session cookie - headers already sent by (output started at /var/www/joomla/libraries/joomla/session/session.php:423) in **/var/www/joomla/libraries/joomla/session/session.php** on line **423**

**Warning**:  session_start() [[function.session-start]("http://localhost/joomla/installation/function.session-start")]: Cannot send session cache limiter - headers already sent (output started at /var/www/joomla/libraries/joomla/session/session.php:423) in **/var/www/joomla/libraries/joomla/session/session.php** on line **423**

**Warning**: Cannot modify header information - headers already sent by (output started at /var/www/joomla/libraries/joomla/session/session.php:423) in **/var/www/joomla/libraries/joomla/session/session.php** on line **426**and in the joomla part itself is the message:

> Cookies do not appear to be enabled on your browser client. You will not be able to install the application with this feature disabled. Alternatively, there could also be a problem with the server's **session.save_path**. If this is the case, please consult your hosting provider if you don't know how to check or fix this yourself.                                                      :confused:

---

### Post by mangurt on 2009-08-21
You need to be in root in order to set the mysql password

```
sudo mysql -u root
```

Also, the previous link was for setting up joomla 1.0  If you are setting up joomla 1.5, then follow this guide.
[HTML]https://help.ubuntu.com/community/Joomla%201.5[/HTML]

---

### Post by Kezz Kezz on 2009-08-21
cheers, will let you know.......

---

### Post by johnocon999 on 2009-09-01
**KEZZ KEZZ** I am a newbie as well and this was a real pain in the *** for me to. Had lots of permission problems but eventually figured it all out after hours of sweat and tears.  Hope this helps you.

I know this might be annoying but firstly remove your current installation of lampp and joomla. just go to the console and do the following: **rm -rf /opt/lampp**

I know its not windows but turn off your machine and restart.

Heres what I done next and I have joomla installed successfully.

[SIZE=4]**Installing xampp 1.7.1 and Joomla under ubuntu 9.04 Linux.**[/SIZE] (by johnocon999)


[SIZE=3]**Installing xampp**[/SIZE]
-----------------
1: Download xampp 1.7.1 for Linux to your desktop. **[SIZE=4]NB: IT MUST BE XAMPP 1.7.1[/SIZE]**  Download from here - [http://sourceforge.net/projects/xampp/files/XAMPP Linux/]("http://sourceforge.net/projects/xampp/files/XAMPP%20Linux/")

2: Extract to /opt folder in your **system files area**.  The best method of doing this is to do it through the console.  You seem to get more permission problems when you dont do it through the console. (I tried it a thousand times from the desktop without complete success. It will extract but will not run without errors).

Use the following command - **sudo tar xvfz xamp-linux-1.7.1.tar.gz -C /opt**

3: To start the server do the following in your console.  **sudo /opt/lampp/lampp start**

4: All services should start.  
-To stop the server running **sudo /opt/lampp/lampp stop**  
-or to restart if its already running **sudo /opt/lampp/lampp restart**

5: To check your installation open browser window and type **[http://localhost](http://localhost)**  (If the installation was successful you should see xampp main page. Choose your language.  Check to see all is working correctly. Check to see that you can enter the myphpadmin section of xampp and create a database without any errors. Hopefully success!


**[SIZE=3]Installing vsftpd (ftp server)[/SIZE]**
------------------
I know ftphd comes with xampp. But I found it easier to configure vsftpd (as I am a novice)
1: Open System > Administrator > Symantic packet manager and search for and install vsftphd
2: To configure vsftpd open the following file **/etc/vsftpd.conf** to change the default settings.

---------------------------------------------------------------------------------------------------------------------
When you open the file just remove the hash symbol from infront of the following commands
**#Local_enable=yes**  (by uncommenting this you will be able to log into ftp using your linux username and password)
**#write_enable=yes**  (will allow you to download and upload files)
---------------------------------------------------------------------------------------------------------------------

The configuration file consists of many configuration parameters. The information about each parameter is available in the configuration file. Alternatively, you can refer to the man page, man 5 vsftpd.conf for details of each parameter.

To run the vsftpd daemon use the following command:

 **sudo /etc/init.d/vsftpd start **

Hopefully success.


**[SIZE=3]Installing Joomla[/SIZE]**
-----------------

1: Download latest version of Joomla from joomla.org

2: The Joomla archive you just downloaded will have to be extracted to the** /opt/lampp/htdocs/** folder. Open up console window and type **sudo nautilus**. Now go to the **opt/lampp/htdocs** and Create a folder called **myjoomlasite**. Right click on folder and set permissions **OWNER ROOT CREATE AND DELETE FILES, GROUP ROOT CREATE AND DELETE FILES Allowing executing - NO**. If you are not able to extract to this folder after changing the permissions. Open the sharing tab and SHARE the folder. You should now be able to extract the archives contents to Myjoomlasite.

3: To see if your installation was successful so far, open browser window and type **[http://localhost/myjoomlasite](http://localhost/myjoomlasite)** and press return.  Hopefully you will be brought to the index.php page and be able to start setting up your joomla site. NB: Make sure no sql errors are displayed at the top of the page.

4: Before proceeding anymore open your xampp server **[http://localhost/xampp](http://localhost/xampp)**, click on **myphpadmin **and create a mysql database to use with your site. setup a user name for the database under the privileges section and grant all privileges click go.  Your database should now be setup.

5: Go back to your joomla setup and continue with the following steps

-** select language** >next
-** pre installation **check (this checks if all the minimum system requirements are met) >next
-** Licence** >next
- **Database** (enter database details)
      Database type: MYSQL 
    Host:Localhost 
    Database Username:
    Password:
    Database Name: (what u called your joomla database)
        >next.
-** FTP LAYER** has to be setup if you wish to add components to joomla under linux. We have already setup vsftpd so this should be a breeze.  You will be required to enter a USERNAME,PASSWORD AND FTP PATH. Username is your linux username:**** password is your linux username password) In order to get the ftp path click Auto find path.  Hopefully your path will have being found eg /myjoomlasite
>next

- **CONFIGURATION **   - by default the username is admin.  And the password is the password you set. The rest is self explanatory
>next

- Before you do anything else you must remove the installation directory from your myjoomlasite folder. Go to **/opt/lampp/htdocs/myjoomlasite **and delete the installation directory.

*you should now be able to login into your sites administrator section.*  To view your site go to **[http://localhost/myjoomlasite](http://localhost/myjoomlasite)**

Hope this tutorial has being of use.   I was hours trying to work this out as Im new to Linux (only a week). And I love it!

---

