---
title: "I am a newbie, and I watch movies in Ubuntu using the movie player"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by didkaticos on 2010-07-01
[FIRST MISTAKE: IT MUST SAY ***I am a newbie and I _[COLOR=Red]WANT[/COLOR]_ to watch movies in Ubuntu using the movie player***] Sorry!

OK, yes, I already said everything: I am a newbie, in his 40's, not a geek, not a good English speaker. Those are my disadvantages. I am 100% fan of Ubuntu, eager to learn, and hater of Windows (which, by the way, I must use at work): these are my strengths.

The only two things that had stopped my of being a 100% Ubuntu user are iPhone (iTunes) and not being able to play DVDs using the movie player. The iPhone issue is already solved: I synchronize it at my office. So, the only thing left is the DVD issue.

I tried to set up the player a couple of months ago. I look on the Internet, here at the forum, and also from some other place (I don't remember the name), and I followed some suggestions. It didn't work. My Ubuntu crashed couple of weeks ago (about the same time that the Ubuntu 10.04 was released. My problem: kernel panic). I tried to get some help from this forum (now I cannot find my post), but I had to un-installed it, and installed it again. It was a pain: I lost a lot of documents, besides the set-up. But I still like Ubuntu, even if I had to deal with some issues.

If someone can help me with some simple suggestions about what is the easiest way to set up the movie maker to be able to play DVDs. I am still with the old Ubuntu System: Ubuntu 9.10 - the Karmic Koala. I got a little afraid after last kernel panic: I remember that I had to do an update, and crash happened afterwards.

Please don't tell me to enter manually any kind of data unless it is totally necessary. If I could get snapshots, it would be easier. 

Thanks a lot for your help, and thanks a lot to Ubuntu, and the Ubuntu community.

didkaticos

---

### Post by kerry_s on 2010-07-01
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by radixx on 2010-07-01
this should explain everything for you    [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jmszr on 2010-07-01
Didkaticos,

I can help you, but using the Terminal will be required. This will not be difficult, it will be a simple matter of copy & paste in the terminal and entering your user password. Here is a simple, reassuring guide to the Terminal: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) .

Ok, now to your issue.  First open the terminal- Applications > Accessories > Terminal. Now copy and paste the following command into the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```
and press Enter.
When it asks for your password, type it in (you will not see it - that's for security) and press Enter. That's it!!

Now do the same for this command: 

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

That should set up your movie player to run DVD's.

I would also suggest installing VLC and smplayer-both should be avaliable in the Software Center or if you are feeling more comfortable with the terminal use it. Example: sudo apt-get install vlc . I only suggest those as a matter of personal preference.

Feel free to ask any questions you might have.

---

### Post by Whistling Nixie on 2010-07-01
^^^ Being an Ubuntu n00b myself, I followed the instructions from that link, only to get a message saying "No URI handler implemented for DVD." What's that about?

---

### Post by iNaitvad on 2010-07-01
Hi, you could install VLC, it should be on the Ubuntu Software  Center, just open de Software Center and search "vlc". It will play everything, you can also install restricted extras from the repositories, but I recomend you to use Ubuntu Tweak. The choose restritec-extras, etc.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Hope it Helps, btw, sorry for my bad english, i speak spanish.

---

### Post by qwerty2009 on 2010-07-01
ARGH why dont anyone use the *help and support* from there system menu?

open terminal from accesories and enter

"sudo apt-get install ubuntu-restricted-extras"

"sudo /usr/share/doc/libdvdread4/install-css.sh"

without quotes

---

### Post by QIII on 2010-07-02
> **qwerty2009 said:**
> ARGH why dont anyone use the *help and support* from there system menu?

Telling a newcomer to RTFM and then not considering that the FM would itself be confusing to a newcomer is not particularly helpful.  It is also quite likely that the OP did not know the FM even existed.

Two posters already pointed the OP to some good documentation and he is free to ask further questions as he has the need.  Snide remarks have a tendency to reinforce the stereotype of the Linux Snob.

By the way, you should have used "doesn't" and "their".  Are you please that I am a grammar snob?

---

### Post by -kg- on 2010-07-02
Not having used "libdvdread4/install-css.sh", I'm not sure how it works.  However, I certainly have used Medibuntu's "libdvdcss2" from the link that kerry_s posted, and it has worked flawlessly for me.

It's not real hard...just follow the instructions from:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

...and you'll be watching DVDs in no time.  You'll also gain access to other interesting (but "non-free") software, like Google Earth and others.  It's totally up to you, though.

It ***is*** a very good thing to install "ubuntu-restricted-extras" from the repository, though.  That contains many codecs that you will likely want to have.

It's automatic for me, now.  Once I install Ubuntu and apply the updates, I install ubuntu-restricted-extras, then Medibuntu and libdvdcss2.  Then I go from there.

---

### Post by didkaticos on 2010-07-02
Thanks a lot for your replies! Let's see...

> **jmszr said:**
> Didkaticos,

I can help you, but using the Terminal will be required. This will not be difficult, it will be a simple matter of copy & paste in the terminal and entering your user password. Here is a simple, reassuring guide to the Terminal: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) .

Ok, now to your issue.  First open the terminal- Applications > Accessories > Terminal. Now copy and paste the following command into the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```and press Enter.
When it asks for your password, type it in (you will not see it - that's for security) and press Enter. That's it!!

Now do the same for this command: 

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```That should set up your movie player to run DVD's.

I would also suggest installing VLC and smplayer-both should be avaliable in the Software Center or if you are feeling more comfortable with the terminal use it. Example: sudo apt-get install vlc . I only suggest those as a matter of personal preference.

Feel free to ask any questions you might have.

I had used this with the terminal the first time, and it didn't work.

> **iNaitvad said:**
> Hi, you could install VLC, it should be on the Ubuntu Software  Center, just open de Software Center and search "vlc". It will play everything, you can also install restricted extras from the repositories, but I recomend you to use Ubuntu Tweak. The choose restritec-extras, etc.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Hope it Helps, btw, sorry for my bad english, i speak spanish.Thanks iNaitvad! I didn't know that VLC works in Ubuntu, and I like it too: this was the one that I was using in Windows. I installed it, but it doesn't play anything. So, do I need to do the terminal thing to being able to use VLC?

I am also a Spanish speaker. By the way: is there any section here where we can use Spanish? I know that some other forums rules doesn't allow any other language besides English.

Last question: how can I call the attention of a moderator to change the name of the thread? As you saw, I made a mistake. I went to bed last night thinking that nobody would open a thread with a tittle like mine :redface:.

Thanks again for your help!

[COLOR=Blue]**NOTE:**[/COLOR]

after I decided to run the terminal thing I did it, and then I had this on my screen. When I tried to close it, I received this warning. Do you know what's going on here?

---

### Post by nothingspecial on 2010-07-02
You hadn`t finished setting java up. You need to press the Tab key to move the red highlight in the java license to ok then press enter.  Then the installation will continue.

It`s not very obvious I suppose.

---

### Post by mkvnmtr on 2010-07-02
If you search in google foros Ubuntu I am sure you will find a spanish language foro to get help in your native language. If you are not in a spanish speaking country you might need to set the advanced search to give results in espanol.

---

### Post by didkaticos on 2010-07-02
> **nothingspecial said:**
> You hadn`t finished setting java up. You need to press the Tab key to move the red highlight in the java license to ok then press enter.  Then the installation will continue.

It`s not very obvious I suppose.No, it wasn't not very obvious, at least for me. And now, I tried to use the terminal again, and I received this. I think I will try again tonight: right now I am about to watch the soccer game, and nothing is more important at this time for me.

Thanks for your help!

---

### Post by nothingspecial on 2010-07-02
It looks like you either have software centre, synaptic package manager or update manager open.

You can only have one open at a time because they are all the same thing.

---

### Post by didkaticos on 2010-07-02
OK, it seems more difficult that what I thought at the beginning. I shutdown my PC, and then turned on again. I tried to do again the ***Termina****l*** stuff, but now I am receiving this message:

[COLOR=Red]*dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.*[/COLOR]

What do I need to do now? I warned you: I didn't want to mess it up with the terminal. I think I have a very bad luck with this kind of stuff.

Any suggestion would be very helpful.

Thanks in advance.

---

### Post by jmszr on 2010-07-02
didkaticos,

You need to run:

```
sudo dpkg --configure -a
```

in the terminal. You are doing fine with the terminal. I know it's kind of scary at first, but as long as you take it one step at a time you will be fine.

---

### Post by didkaticos on 2010-07-02
> **jmszr said:**
> didkaticos,

You need to run:

```
sudo dpkg --configure -a
```in the terminal. You are doing fine with the terminal. I know it's kind of scary at first, but as long as you take it one step at a time you will be fine.Thanks a lot for your suggestion and your confidence jmszr! OK, I ran that on the terminal, and now I am seeing this:

> [COLOR=Red]luis@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for luis: 
Setting up java-common (0.30ubuntu5) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
luis@ubuntu:~$ [/COLOR]

What's next? Do I need to run again this? :confused:

```
sudo apt-get install ubuntu-restricted-extras 
```

Cursor is blinking and ready, as well as me. I mean, I am not blinking, but I am ready :D.

Thanks a lot for your help!

---

### Post by jmszr on 2010-07-02
didkaticos,

I believe that you just finished setting up java and therefore you finished installing ubuntu-restricted-extras. Just to be on the safe side why don't you run it again - just to be sure. It won't harm anything and then you'll _know_ it's completely installed.

Then, if you haven't already, you need to run the:

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```
command.

---

### Post by Palanthas on 2010-07-02
I used to be worried about messing up my computer by using the terminal but found that it really isn't that difficult.

I want to encourage you here; it is not that difficult, and you can (and I hope, will) get there! :D

OK, pep talk over. ;)

---

### Post by didkaticos on 2010-07-02
> **jmszr said:**
> didkaticos,

I believe that you just finished setting up java and therefore you finished installing ubuntu-restricted-extras. Just to be on the safe side why don't you run it again - just to be sure. It won't harm anything and then you'll _know_ it's completely installed.Something weird is happening again. I tried to run it again, and this is what I got:

```
luis@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for luis: 
Setting up java-common (0.30ubuntu5) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
luis@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for luis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
luis@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
luis@ubuntu:~$ 
```Another thing is that I hadn't realized that I had some software updates ready to be installed :confused:.

Help!

---

### Post by iNaitvad on 2010-07-02
Esta instalando Java, dale aceptar, no habra problemas, espero que no me maten por escribir en español, puedes enviarme un mensaje por privado para agregarte al messenger, o algo por el estilo. Es raro que el VLC no reproduzca, yo lo que hago es abrir el .ifo que esta dentro de la carpeta VIDEO_TS en el DVD, o sino dale MEDIO/ABRIR DISCO.
Hay muchas aplicaciones por instalar en Ubuntu Tweak, te recomiendo que lo instales. Saludos, espero que te sirva.

P.D: Sorry for my bad spanish, jajaja

---

### Post by jmszr on 2010-07-02
didkaticos,

You need to put "sudo" in front of "apt-get -f install":

```
sudo apt-get -f install
```.
Try that.

---

### Post by col48 on 2010-07-02
To my eye, I think the last apt-get -f install would need to be

sudo apt-get -f install

to run it as superuser/administrator.  Each command you want to run as superuser needs its own sudo before it unless you have opened a root terminal (which is not usually appropriate)

---

### Post by didkaticos on 2010-07-02
> **iNaitvad said:**
> Esta instalando Java, dale aceptar, no habra problemas, espero que no me maten por escribir en español, puedes enviarme un mensaje por privado para agregarte al messenger, o algo por el estilo. Es raro que el VLC no reproduzca, yo lo que hago es abrir el .ifo que esta dentro de la carpeta VIDEO_TS en el DVD, o sino dale MEDIO/ABRIR DISCO.
Hay muchas aplicaciones por instalar en Ubuntu Tweak, te recomiendo que lo instales. Saludos, espero que te sirva.

P.D: Sorry for my bad spanish, jajajaGracias por la sugerencia! Voy a tratar primero de arreglar este enredo en el que meti.

> **jmszr said:**
> didkaticos,

You need to put "sudo" in front of "apt-get -f install":

```
sudo apt-get -f install
```.
Try that.
But do I need to update first? Or it doesn't matter? Did you see the screenshots that I posted? Here are them again. I am a little worried about that warning with the Package Manager: "An error occurred, please run Package Manager yada yada yada...".

---

### Post by jmszr on 2010-07-02
didkaticos,

Go ahead and run that command - it might clear up the Package Manager situation. We'll see what the outcome of entering the command is and go from there.

---

### Post by didkaticos on 2010-07-02
It doesn't look good to me:

```
luis@ubuntu:~$ luis@ubuntu:~$ sudo dpkg --configure -a
luis@ubuntu:~$: command not found
luis@ubuntu:~$ [sudo] password for luis: 
[sudo]: command not found
luis@ubuntu:~$ Setting up java-common (0.30ubuntu5) ...
bash: syntax error near unexpected token `('
luis@ubuntu:~$ 
luis@ubuntu:~$ Processing triggers for man-db ...
Processing: command not found
luis@ubuntu:~$ Processing triggers for doc-base ...
Processing: command not found
luis@ubuntu:~$ Processing 2 added doc-base file(s)...
bash: syntax error near unexpected token `('
luis@ubuntu:~$ Registering documents with scrollkeeper...
Registering: command not found
luis@ubuntu:~$ luis@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
luis@ubuntu:~$: command not found
luis@ubuntu:~$ [sudo] password for luis: 
[sudo]: command not found
luis@ubuntu:~$ Reading package lists... Done
Reading: command not found
luis@ubuntu:~$ Building dependency tree       
Building: command not found
luis@ubuntu:~$ Reading state information... Done
Reading: command not found
luis@ubuntu:~$ You might want to run `apt-get -f install' to correct these:
> The following packages have unmet dependencies:
>   sun-java6-jre: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed or
>                           ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed
>                  Recommends: gsfonts-x11 but it is not going to be installed
> E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
> luis@ubuntu:~$ apt-get -f install
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
> E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
> luis@ubuntu:~$ luis@ubuntu:~$ sudo dpkg --configure -a
> [sudo] password for luis: 
> Setting up java-common (0.30ubuntu5) ...
> 
> Processing triggers for man-db ...
> Processing triggers for doc-base ...
> Processing 2 added doc-base file(s)...
> Registering documents with scrollkeeper...
> luis@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
> [sudo] password for luis: 
> Reading package lists... Done
> Building dependency tree       
> Reading state information... Done
> You might want to run `apt-get -f install' to correct these:
> The following packages have unmet dependencies:
>   sun-java6-jre: Depends: sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed or
>                           ia32-sun-java6-bin (= 6.20dlj-0ubuntu1.9.10) but it is not going to be installed
>                  Recommends: gsfonts-x11 but it is not going to be installed
> E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
> luis@ubuntu:~$ apt-get -f install
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
> E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
> luis@ubuntu:~$ 
```

Do I need to Restart, and start all over again? Or it would be better to go to bed and take a nap?

---

### Post by jmszr on 2010-07-02
didkaticos,

You forgot to put the "sudo" in front of "apt-get -f install" 

Try that. Nap is up to you, but it does sound like a pleasant idea.

---

### Post by didkaticos on 2010-07-02
> **jmszr said:**
> didkaticos,

You forgot to put the "sudo" in front of "apt-get -f install" 

Try that. Nap is up to you, but it does sound like a pleasant idea.OK jmszr: I decided to start from scratch. So, I shutdown my PC, and went to bed. ERROR: I couldn't take a nap. Then I started again Ubuntu, installed all the updates, and then start from the beginning at the terminal:
```

luis@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for luis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libfaac0 libmjpegtools-1.9 libmp3lame0
  libmp4v2-0 libquicktime1 libxvidcore4 sun-java6-plugin ttf-liberation
  ttf-mscorefonts-installer unrar
The following NEW packages will be installed:
  cabextract gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse libfaac0 libmjpegtools-1.9 libmp3lame0
  libmp4v2-0 libquicktime1 libxvidcore4 sun-java6-plugin ttf-liberation
  ttf-mscorefonts-installer ubuntu-restricted-extras unrar
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2,826kB of archives.
After this operation, 6,865kB of additional disk space will be used.
Do you want to continue [Y/n]? y

[...]

Setting up ubuntu-restricted-extras (36) ...
Setting up unrar (1:3.9.3-1) ...
update-alternatives: using /usr/bin/unrar-nonfree to provide /usr/bin/unrar (unrar) in auto mode.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
luis@ubuntu:~$
```Then:

```
luis@ubuntu:~$  sudo /usr/share/doc/libdvdread4/install-css.sh
--2010-07-02 19:59:03--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37252 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-nsSmvJ/libdvdcss.deb'

100%[=======================================================================================================================================>] 37,252      72.5K/s   in 0.5s    

2010-07-02 19:59:04 (72.5 KB/s) - `/tmp/dvdcss-nsSmvJ/libdvdcss.deb' saved [37252/37252]

Selecting previously deselected package libdvdcss2.
(Reading database ... 145088 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-nsSmvJ/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
luis@ubuntu:~$
```**[SIZE=6][COLOR=Magenta]And now I am watching a movie on the Movie Player[/COLOR][/SIZE]****[SIZE=6][COLOR=Magenta]![/COLOR][/SIZE]****[SIZE=6][COLOR=Magenta] :popcorn: [/COLOR][/SIZE]**

Thank you so much for your help!

NOTE: so I think that, at the end, this thread has the_ right name_: [B]I am a newbie, and I watch movies in Ubuntu using the movie player ;).
[/B]

---

### Post by jmszr on 2010-07-02
didkaticos,

You're welcome. And good for you, you've gotten your movie player working and you did it using the Terminal.
Not so bad using the terminal after all, is it?

---

