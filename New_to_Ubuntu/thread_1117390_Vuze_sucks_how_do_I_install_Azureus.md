---
title: "Vuze sucks how do I install Azureus?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-04-05
Hi,

On Hardy Heron I had Azureus.  I have recently upgraded to Intrepid Ibex.  When I run: 

```
sudo apt-get install azureus
```

It installs Vuze.  Vuze sucks how do I find an old version of Azureus?

---

### Post by Hospadar on 2009-04-06
You could get one from the azureus website, but I hardly see the need.  There are a plethora of great torrent clients for linux.

Transmission comes installed by default, I use it on my server box and love it, you could also try deluge, ktorrent, and there are more if you search around.

For normal desktop use I really prefer deluge, but I like transmission's web client a little better (although deluge has a very excellent web client)

---

### Post by asmoore82 on 2009-04-06
[COLOR="Blue"]Azureus **is** now Vuze:[/COLOR] [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by kdreimiller on 2009-04-06
i use deluge.  a few more bells and whistles than transmission.  and vuze (azureus) was always trying to update itself without ever updating and drove me nuts.

---

### Post by lovinglinux on 2009-04-06
You can turn off all that Vuze stuff, by choosing the basic interface. I don't remember exactly how to do this, but it shouldn't be hard to find this option. It will look exactly like Azureus.

I used Azureus for a long time, but since I installed Deluge I never looked back.

---

### Post by Captain_Glen on 2009-04-06
Can you schedule Deluge.  I can't figure out how.

---

### Post by lovinglinux on 2009-04-06
> **Captain_Glen said:**
> Can you schedule Deluge.  I can't figure out how.

The old version (0.5.x) has a scheduler plugin, but I'm afraid the new one (1.x.x) doesn't. Anyways, you can download 0.5.x series at [http://download.deluge-torrent.org/archive/ubuntu/](http://download.deluge-torrent.org/archive/ubuntu/)

I was using version 0.5.8.9 until 2 days ago and it worked like a charm. Version 0.5.9.4 is the last version of the 0.5 series.

---

### Post by madverb on 2009-05-08
Even though this thread is a bit old I thought I would give you an update. Although the scheduler hasn't been ported to version 1 of Deluge you can schedule download periods another way.
```
sudo apt-get install gnome-schedule deluge-console
```
And then follow this [http://dev.deluge-torrent.org/wiki/UserGuide/Scheduling](http://dev.deluge-torrent.org/wiki/UserGuide/Scheduling)

---

### Post by powel212 on 2009-05-08
Ktorrent is the answer

It does everything. An, it's way lighter than Vuze.

P.

---

### Post by Chemical Imbalance on 2009-05-08
Deluge and Ktorrent are my favorites.  
They are both lightweight and have DHT.

---

### Post by PsySc0rpi0n on 2009-05-13
I would also like to install Azureus aka Vuze...

I have Vuze 3.1.1.0 and everytime i start Vuze it asks for an update that i downoad but i can't instal it... It's a JAR file (Azureus4203-B18.jar). Then i download commons-cli.jar and log4j.jar and placed all 3 files in the same folder.

Than i started the console, entered in the folder and performed the following command:

java -jar Azureus4203-B18.jar --ui=console

The process starts to run but i guess that it never comes to an end because the console should finish the process and show the folder path and it doesen't...

My console after the command satys like this for ever

```

psysc0rpi0n@psysc0rpi0n-desktop:~/Documentos$ java -jar Azureus4203-B18.jar --ui=console
file:/home/psysc0rpi0n/Documentos/Azureus4203-B18.jar ; file:/home/psysc0rpi0n/Documentos/

Core Start Completed
ConsoleInput: initializing...
Attempting to load aliases from: /home/psysc0rpi0n/.azureus/console.aliases.properties
ConsoleInput: initialized OK
ConsoleInput: starting...
ConsoleInput: started OK
Running Vuze 4.2.0.3_B18...
Using configuration settings from:
  /home/psysc0rpi0n/.azureus/
> -----
Available console commands (use help <command> for more details):

  [] xml   [#] hack   [a] add   [c] check   [q] queue   [r] remove   
  [s] start   [h] stop   [] host   [] publish   [] forcestart   [tl] tlog   
  [l] log   [m] move   [] share   [+] set   [sh] show   [u] ui   [] logout   
  [] quit   [?] help   [] alias   [] prio   [] plugin   
> -----
DEBUG::Wed May 13 22:34:16 WEST 2009::org.gudy.azureus2.core3.internat.IntegratedResourceBundle::handleGetObject::265:
  Failed to load message bundle scratch file
    ResourceBundle::getObject::396,ResourceBundle::getString::362,MessageText::getResourceBundleString::318,MessageText::getString::285,TrackerStatus::updateSingleHash::256,TrackerStatus::updateSingleHash::201,TrackerChecker::runScrapes::323,TrackerChecker::access$000::37,TrackerChecker$1::runSupport::69,AEThread::run::74
java.io.FileNotFoundException: /home/psysc0rpi0n/.azureus/tmp/AZU9181322569686801726.tmp (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at org.gudy.azureus2.core3.internat.IntegratedResourceBundle.loadMessages(IntegratedResourceBundle.java:466)
    at org.gudy.azureus2.core3.internat.IntegratedResourceBundle.handleGetObject(IntegratedResourceBundle.java:265)
    at java.util.ResourceBundle.getObject(ResourceBundle.java:396)
    at java.util.ResourceBundle.getString(ResourceBundle.java:362)
    at org.gudy.azureus2.core3.internat.MessageText.getResourceBundleString(MessageText.java:318)
    at org.gudy.azureus2.core3.internat.MessageText.getString(MessageText.java:285)
    at org.gudy.azureus2.core3.tracker.client.impl.bt.TrackerStatus.updateSingleHash(TrackerStatus.java:256)
    at org.gudy.azureus2.core3.tracker.client.impl.bt.TrackerStatus.updateSingleHash(TrackerStatus.java:201)
    at org.gudy.azureus2.core3.tracker.client.impl.bt.TrackerChecker.runScrapes(TrackerChecker.java:323)
    at org.gudy.azureus2.core3.tracker.client.impl.bt.TrackerChecker.access$000(TrackerChecker.java:37)
    at org.gudy.azureus2.core3.tracker.client.impl.bt.TrackerChecker$1.runSupport(TrackerChecker.java:69)
    at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:74)



```

"DEBUG::Wed May 13 22:34:16 WEST 2009::org.gudy.azureus2.core3.internat.IntegratedResourceBundle::handleGetObject::265:
  Failed to load message bundle scratch file"

Is that error normal? 


And when i try to close the console it says to me that there is a process running and if i close the console the process will bi killed...

---

### Post by MontelEdwards on 2009-05-13
OK. If you just download the file from the Vuze website... and double click on Vuze.. it works fine. No terminal required. And to the OP: Vuze is the new name.

---

### Post by PsySc0rpi0n on 2009-05-14
Hello...

Well i downloaded Vuze from its website and it was a tar.bz2 file. I extracted it into a folder but when i ask to "Open-Execute in Console (or just Execute)" the Azureus file that is in the extraced folder, nothing happens.

How can i solve this???

Edit;

Switched to Deluge... Looks a lot like Windows uTorrent and is simple to use...

---

### Post by jjosotoro on 2009-06-02
ok your problem is something a lot of people is passing trougth whit ubuntu jaunty, the way i solved it was very simple and actually gave me acces to other aplications i use a lot; what i did was adding the getdeb repository to mi list

echo "deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/" | sudo tee -a /etc/apt/sources.list.d/getdeb.list && sudo apt-get update

now if that gives an gpg error like this:

W: GPG error: [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

you must use the following command in the terminal:

gpg --keyserver hkp://subkeys.pgp.net --recv-keys "XXXXXXXXXX"
sudo gpg --export --armor "XXXXXXXXXX" | sudo apt-key add -
sudo apt-get update

replacing the "XXXXXXXXXX" whit the number that appears in the message ex: B152F042D246C25D

$sudo apt-get update

just to check about the gpg error (it shouldnt appear anymore)

$sudo apt-get install vuze

this will install the version of vuze that is on getdeb (4.2.0.2) whit all dependencies, or you can install it using synaptics.

$sudo chmod -R 777 /usr/share/vuze

this will let vuze to do any upgrade

---

### Post by trooperchix on 2009-06-28
jjosotoro... you rock.  all the millions of ways I've been trying to get vuze to work on jaunty...  this worked.  it is unweildly, but I like the search function integrated.  Thanks!!

---

### Post by lulu135 on 2009-10-05
I think for certain applications, especially apps with built-in update features, it's easier to avoid using the package manager and just download the offical release and untar it in a directory somewhere.
Then you can just create a shortcut to the main binary or run it from the command line.

The problem with installing it as root using apt-get is that the self-update never works and you have to wait for your distro to create a new package before you can upgrade.  If you use the Vuze's own release then you can always have the latest version whenever you want, and if you want to uninstall it's as easy as rm -rf vuze/

---

