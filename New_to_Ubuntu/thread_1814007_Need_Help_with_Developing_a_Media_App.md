---
title: "Need Help with Developing a Media App"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Media Anywhere on 2011-07-28
Hello,

I am very new to the Linux world.  Let me give you a quick run down of what I would like to do and in turn I am hoping that some of you might be able to point me in the right direction.

I want to build a web app/page that I can access from any mobile device or from the web period.  The application is a media app which will allow me access to all my audio and video files.  The reason for the app is I have just shy of 1 TB of audio and I currently run my pc through my house stereo, without using itunes I would like to be able to control my media through the house by using an app that is customized to my needs and also not running down to the basement to lower it or change the song, etc :)

I have basic requirements written up but I am sure they will change as this project hits certain milestones.

I think I need the following:

1. some sort of Dev tool to build the web page.
2. some type of DB where I can transfer all my data to.

Problem is I have no idea where to start in fact i don't even know the technically end of building anything like this but I am going to give it a shot.

Thx

Kev

---

### Post by lkjoel on 2011-07-28
You could have a local web server on your media computer, having a PHP file that is an interface to some other applications on that computer, which then the applications change the volume/change the song etc...

I could help you make it if you would like.

---

### Post by jerrrys on 2011-07-28
i take lkjoel up on that offer.  but got to ask one thing.  wouldn't [remote access]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remote+access&sa=Search&cof=FORID:9#956") be an easier way to go?

---

### Post by lkjoel on 2011-07-28
> **jerrrys said:**
> i take lkjoel up on that offer.  but got to ask one thing.  wouldn't [remote access]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remote+access&sa=Search&cof=FORID:9#956") be an easier way to go?
lol yeah. I always forget the simple ways...

---

### Post by fdrake on 2011-07-28
so you want to develop some kind of web controller for your music media. I'd agree with lkjoel that the easiest way is PHP website with a database. Sounds like a fun idea. I'd like to contribute if you'd like! :)

ps: do you plan to use it only inside your home-network or also outside your house, like controlling from the office etc..?


remote access from a phone would not work! plus it's like cheating...  :D

---

### Post by Media Anywhere on 2011-07-28
@ lkjoel ok where do I start?  PHP??? what do I need to get started?

All help is welcome, once I finish the requirements I'll email them over.

@ jerrys   yes I suppose remote access would work but I dont want to be limited to what is currently out there.

@ fdarke YES BUT!!!! there is a major hurdle with that.  The biggest function remotely would include an ardunio (google it) so i can actually turn on and off all my equipment and then control the app we develop using the website. So part of the site will be controlling the database of media and the other part is actually controlling hardware remotely.

Question to all it seems I need to make a PHP website, which dev tool should i use?  and to all where do i start?

Many Thanks

---

### Post by fdrake on 2011-07-28
well first you need to install or check apache, mysql, phpMyAdmin,etc
download the sh script (in the Download folder) and run it with
```

cd ~/Downloads
sudo chmod +x apache_php.sh
sudo ./apache_php.sh

```

after the install download the index.php file
```

cd ~/Download
sudo cp index.php /var/www.index.php
firefox localhost/index.php  #to check if php is running
```


edit:i cannot post php file in the forum somehow
so jus write this with a text editor and same as index.php . you'll need sudo to save it in /var/www
```
<?php

echo "Is this a test";

?>
```

---

### Post by Media Anywhere on 2011-07-29
ok that was all successful.  Now what :)

---

### Post by aeiah on 2011-07-29
just use [ampache ]("http://ampache.org/")or [mpd]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki")

control it from your phone/netbook/tablet

---

### Post by fdrake on 2011-07-29
when you go to localhost/index.php with firefox do you see the message. To test that php is running correctly.

well if succesfull than we need to decide what is this app going to do: the objectives:
play/select media? change volume? ask for user login?

---

### Post by Media Anywhere on 2011-07-29
when i run that command it opens firefox and and displays the message is this a test...

---

### Post by fdrake on 2011-07-29
> **Media Anywhere said:**
> when i run that command it opens firefox and and displays the message is this a test...

ok , the server is ready now we have to decide what functions we want to give to the site. What we want it to do? brainstorm.. and objectives

---

### Post by Media Anywhere on 2011-07-29
ok give me the weekend to come up with some type of draft.

Did you google arduino?     [http://www.arduino.cc/](http://www.arduino.cc/)

---

### Post by fdrake on 2011-07-29
that's actually very interesting. it could be a good implementation for this website in the future. less then $50!! not bad at all.

> ok give me the weekend to come up with some type of draft.
ok, in the meanwhile,I'll start doing a template of the site with some simple and generic shell functions. I will post sunday-night or monday morning some stuff.

---

### Post by Media Anywhere on 2011-07-29
sounds great

---

### Post by fdrake on 2011-08-01
ok, this is a first, very basic, draft of the site. For now it only let's you select a song from a list on a web page and plays the song on the remote pc. I will work the next few days (if works permits) on the volume, css, and a search form that lets find a song.  I think this project can grow in a good way.
-------------------------------------------------------------------------
how to make it work:

1. Extract everything in a folder in /var/www or where you server is installed

2.Get few songs together in the same folder. !!! Very important !!!:make sure that there are no spaces in the names or in the path of the files. So for example:
Good ---> /home/josh/music/song.mp3
Bad ----> /home/John Smith/my good song.mp3
This is the first draft, as soon i solve the space and special character issue will let you know

3. ```
sudo chmod -R +xr ./mediAnywhere/
``` # php need permission to read execute files

4.```
sudo chmod -R 777 ./mediaAnywhere/shell
``` #php needs permission to write on input file

5. ```
./mediaAnywhere/shell/reader.sh
``` this program needs to be always runnign (on the background). It checks if there is any input from a php command.

6. ```
./mediaAnywhere/shell/data_to_mysql.sh
``` It creates database and tabel for your song list.(you need to know localhost, user, password). it also imports for you the list of song on a specific folder (instead of inserting data with phpMyAdmin one by one).

7.go to [http://localhost/.../mediAnywhere/media.php](http://localhost/.../mediAnywhere/media.php) and you should see a list of you songs on the webpage. Click on the link to start playing.
--------------------------------------------------------------------------
Issues to be solved in the next draft: 
-Kill a child process when a new child process starts (ex. to stop playing a song after someone selects another song to be played)
-spaces and special characters on the path or name of a file make it a little bit tricky to insert data to mysql with bash
-volume control
-improve design and navigation of the site. (css and images)
--------------------------------------------------------------------------

anyone that wants to contribute is welcome. I think this project can do more than just playing and controlling media remotely, like for example start a back-up process, print files, and running different processes remotely like from your phone or iPod.

---

### Post by Media Anywhere on 2011-08-03
ok give me the next 24 to 48 hours,  thank you.

---

### Post by Media Anywhere on 2011-08-11
i am having the hardest time gaining permission to drop the tar package into my dir tells me i dont have permissions, i am working on it now, so sorry for the delay,  I work for the NYSE and with the markets going nutz the past few days i've been working like a dog.  I will have a complete update and status and req doc over the weekend.

---

### Post by fdrake on 2011-08-11
No rush!  I fixed the script so that you can change the song you are playing,  and  by the end o$ the week I should post a new script with the option to change the  volume and to find songs in a specific folder.
 the permission issue is caused by the fact that the web server is a user itself, it not your user account.

---

### Post by Media Anywhere on 2011-08-11
how can i remedy this so i can add the files to the dir or add the whole folder/dir to the required folder :)?

---

### Post by lkjoel on 2011-08-11
Try this:
```
sudo chmod -R 0777 /var/www

```

---

### Post by Media Anywhere on 2011-08-15
ok with the help of [lkjoel]("http://ubuntuforums.org/member.php?u=1072696") i gained access but now i am getting the following error i believe its on my end tho,  working through it now.

auto-rehash                       TRUE
character-sets-dir                (No default value)
column-type-info                  FALSE
comments                          FALSE
compress                          FALSE
debug-check                       FALSE
debug-info                        FALSE
database                          (No default value)
default-character-set             latin1
delimiter                         ;
vertical                          FALSE
force                             FALSE
named-commands                    FALSE
ignore-spaces                     FALSE
local-infile                      FALSE
no-beep                           FALSE
host                              LinuxServer
html                              FALSE
xml                               FALSE
line-numbers                      TRUE
unbuffered                        FALSE
column-names                      TRUE
sigint-ignore                     FALSE
port                              3306
prompt                            mysql> 
quick                             FALSE
raw                               FALSE
reconnect                         FALSE
socket                            /var/run/mysqld/mysqld.sock
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
table                             FALSE
user                              Kevin
safe-updates                      FALSE
i-am-a-dummy                      FALSE
connect_timeout                   0
max_allowed_packet                16777216
net_buffer_length                 16384
select_limit                      1000
max_join_size                     1000000
secure-auth                       FALSE
show-warnings                     FALSE


CREATE DATABASE media; USE media; CREATE TABLE music (id INT, path VARCHAR(1000), name VARCHAR(1000));  :sql query did not work! kevin@LinuxServer:/var/www/mediaAnywhere/shell$

---

### Post by lkjoel on 2011-08-15
Try this:
```
sudo apt-get install tasksel
sudo tasksel install lamp-server

```

---

### Post by Media Anywhere on 2011-08-16
installed the tasksel and lamp-server   what is the next step?  I tired to create the db again but i received the same message...

---

### Post by lkjoel on 2011-08-17
Try this:
```
cd path/to/media/anywhere
sudo sed -i 's:\$password=.*:\$password="*MYSQLPASSWORD*":g' include/include.php

```

---

### Post by fdrake on 2011-08-17
can you try to login with phpmyadmin?
it should be:
```

localhost/phpMyAdmin

```

---

### Post by Media Anywhere on 2011-08-22
what does this error mean?   (id INT, path VARCHAR(1000), name VARCHAR(1000))

---

### Post by lkjoel on 2011-08-22
Could you give the full error message?

---

### Post by Media Anywhere on 2011-08-23
its the same error actually as above, but i have two other questions.

Does my apache need to be running? and When I run the reader.sh i get 1:22 streaming down my terminal, does that confirm that its running?

If apache needs to be running to create the table (which i don't believe needs to be) how do I start my apache?

---

### Post by lkjoel on 2011-08-23
What does the reader script show?

To start apache:
```
sudo /etc/init.d/apache2 restart

```

---

### Post by Media Anywhere on 2011-08-23
here are two screen shots, one is my dir structure just want to make sure its ok and the second is the 1:22  :)

---

### Post by lkjoel on 2011-08-23
Now I understand. So could you elaborate on the error message that the setup script gives?

---

### Post by Media Anywhere on 2011-08-23
sure i attached it along with the few questions it asks, how can i confirm that the change password script worked correctly :) ?

see attached

---

### Post by fdrake on 2011-08-23
> **Media Anywhere said:**
> sure i attached it along with the few questions it asks, how can i confirm that the change password script worked correctly :) ?

see attached

you cannot use that kind of name. use only 1 word please: like root or kevin. that's why you probably cannot connect/(or create) to the database

ps. the reader.sh script just check sif the input (logfile) has changed and reads its contents. It has nothing to do directly with apache.

---

### Post by Media Anywhere on 2011-08-26
ok so i need to change my user name?

---

### Post by Media Anywhere on 2011-08-26
run that script again i suppose?

---

### Post by Media Anywhere on 2011-09-20
any one around, sorry for the delay???

---

