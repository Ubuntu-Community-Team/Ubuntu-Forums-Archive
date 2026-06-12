---
title: "I cant get HellaNZB and LottaNZB to work"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by BeatnikBandit on 2010-04-11
I have no disallusions about being a beginner I am so this is why Need to use the Gui for HellaNZB. Currently The only way i can download NZB files is with Klibido and i dont really prefer it. Its VERY slow at Decoding files after they are downloaded and then I still have to unRaR them on my own. 

Now I know that HellaNZB can do this all for me automatically and i know that LottaNZB is a Gui Frontend for HellaNZB. I have them both installed the problem is I do not know How to Configure HellaNZB and how to use LottaNZB to control it once i configure it. So Basically I could really use a how to on this. I have been unable to find one on my own (if one exists somewhere) It would help me a lot as Most of the downloading i do is Via Usenet.

I would be very appreciative if anyone can help me with this

---

### Post by new_tolinux on 2010-04-11
I don't know a lot about hellanzb, but I do know sabnzbdplus, which is about the same.

It's in the repositories and can be accessed through the webbrowser (by default at [http://localhost:8080](http://localhost:8080)).

---

### Post by BeatnikBandit on 2010-04-11
I tried to use sabnzbdplus before and idk if its the web interface that i dont like or the configuration of it as when i tried it last it worked then i had trouble getting it to run again and i basically stopped worrying about it as i think i like hellaNZB more although it may be more complicated for some reason to me sabnzbd+ is harder (i am dumb i know)
 
I think i have gotten hellanzb working although i have yet to try an nzb i will in one min after i post what i did in the config file, I hope someone can verify I did it correctly. I think its fine? This all I changed in the hellanzb.conf file from what it says thats all i need to change although i dont know if i did it correctly

```
# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'astraweb',
             hosts = [ 'us.news.astraweb.com:119' ],
             #hosts = [ 'us.news.astraweb.com:119' ],


             username = '*****',
             password = '*****',
             #username = *****,           
             #password = *****,

             connections = 7,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 1500 # limit to 1500kB/s


# Important locations
Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/home/matthew/Incomming/' 
```so as you can see all i changed is i added the usenet server i use, the number of connections, The username and password (although its not posted here it is correct in my file), Lastly I upped the max download speed to my max download speed. I left everything else the same and in case i FUBAB i made a copy of the default conf file.

EDIT: now that i have added an nzb file it will not download so i must have something wrong :cry: WAHHH

---

### Post by new_tolinux on 2010-04-11
As far as I can see, there is nothing in the config what seems to be wrong at first.
But as I said before, I don't know hellanzb, so I'll leave this thread to someone else.

Not because I'm not willing to help, just because it doesn't make sense to me to install a program, hope that it works, and then (still) guess where your problem comes from because I still don't know my way around in the program.

---

### Post by BeatnikBandit on 2010-04-12
basically i need to just set up this file and everything should work in the hopes of someone helping me out i am going to post the unedited conf file and give you my server addy and we will just use username and password for that part. Maybe i will have to use Sabnzbd+ although i don't know how to work that one either so maybe someone can post a link to a howto or tell me how to use it in the mean time ill try to learn sabnzbd+ should HellaNZB not work although it seams to be very easy I just don't know what Is wrong.

So here is the conf file ill post in in code instead of an attachment:

```
# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 1057 2007-03-27 04:13:53Z pjenvey $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = os.path.expanduser('~') + '/.hellanzb/log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = os.path.expanduser('~') + '/.hellanzb/log-debug'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'changeme',
             hosts = [ 'news.changeme.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'changeme',
             password = 'hella',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             #fillserver = 0,            # defaults to 0 (a main server).
                                         # fillservers must have values > 0
                                         # (priority)
             ssl = False
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/.hellanzb/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'done/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True


# Maximum amount of memory used to cache encoded Article data segments.
# hellanzb will write article data to disk when this cache is exceeded
# Available settings:
# -1: Unlimited size
#  0: Disable cache (only cache to disk)
# >0: Limit cache to this size, in bytes, KB, MB, e.g.:
#     1024 '1024KB' '100MB' '1GB'
#Hellanzb.CACHE_LIMIT = 0


# Save archives into a sub directory of DEST_DIR named after their newzbin.com
# category (when queued using the enqueuenewzbin XMLRPC call); e.g. Apps,
# Movies, Music
Hellanzb.CATEGORIZE_DEST = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = True

# Supply a path to the optional macbinconv command (for converting MacBinary
# files)
#Hellanzb.MACBINCONV_CMD = None

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Enable libNotify Daemon notifications
Hellanzb.LIBNOTIFY_NOTIFY = False


# Disable ANSI color codes in the main screen (preserves the in place scroller)
#Hellanzb.DISABLE_COLORS = False

# Disable ALL ANSI color codes in the main screen (for terminals that don't
# support ANY ANSI codes
#Hellanzb.DISABLE_ANSI = False


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# IP address on which the XMLRPC Server will be binded to.
# Type '0.0.0.0' for any interfaces, '127.0.0.1' will disable remote access
Hellanzb.XMLRPC_SERVER_BIND = '127.0.0.1'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to http://www.newzbin.com for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = None
Hellanzb.NEWZBIN_PASSWORD = None


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Support extracting NZBs from ZIP files with this suffix (case insensitive) in
# QUEUE_DIR. Defaults to '.nzb.zip'. Set to False to disable.
#Hellanzb.NZB_ZIPS = '.nzb.zip'

# Support extracting NZBs from GZIP files with this suffix (case insensitive)
# in QUEUE_DIR. Defaults to '.nzb.gz'. Set to False to disable.
#Hellanzb.NZB_GZIPS = '.nzb.gz'

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'
```ok now for the information:

[LIST]
[*]I would like it to place the files in this directory: /home/matthew/Incomming
[/LIST]

[LIST]
[*]My news server info is: us.news.astraweb.com:119 It requires a username and password and the name of the server is of no issue to me it could be astraweb, news, usenet, whatever works.
[/LIST]

[LIST]
[*]My max speed is 1.5MB a sec
[/LIST]

I think thats all the information needed PLEASE tell me if you need anything else (besides my username and pass. I also can connect via SSL but for right now i am not worried about it i am more worried about making it work if someone is great they could set up for me one conf file for ssl and one without here is the ssl server: ```
ssl.astraweb.com Ports 443 or 563
``` the only difference except whatever needs to be in the conf file.  This is my first time configuring a conf file so this is very helpful for me if someone can help me.  I promise i will pay it forward i will answer any question i feel i can answer correctly. I would even consider donating $5 to a charity of your choice i need help! Lastly thank you to those that posted trying to do their best with helping me!!!!

---

### Post by BeatnikBandit on 2010-04-13
This is an update i just did not want my last post to become larger as it is now the main subject of the thread. Should I change it to the OP??

Well I have decided that since i cant get hellaNZB working (although i still want to remember that i have not given up on it) I have decided to quit beating myself with Klibido (i don't even use KDE so its going away from my pc ASAP) and try to start treating myself with Sab.

So now am using 2 programs for the **Usenet** *Sabnzbd+ and Pan.* Sab for .nzb files and Pan for basic browsing and downloading non .nzb files. This is fine although i want it to be HellaNZB and Pan. (I like the Pan Project although they need to add nzb processing to keep up)

So currently I am doing fine with sab although i am still on a quest to use HellaNZB because i HATE apps that ONLY have a web interface. As I am using an older computer ```
Dell Insperion 1100, 2 ghz CPU, 166mhz FSB, 512 Megs Memory, 128 shared with a crappy Intel Graphics card, no internal WiFi, i Use a PCMCIA WiFi card /w MIMO
``` It doesn't work to well. So yeah you get the picture and using it with firefox, the program works but it is more like set forget and hope because the monitoring of the file progress is terrible (for me i am not bashing the program i Know MANY LOVE it, actually without it i would still be suffering greatly with Klibido, Web UI's are just not my bag.) I just prefer a GUI if available usually they are much faster getting information and showing it from a daemon IMO, although i like having a Web interface to remotely download I just wish there was a Gui for Sab IDK why Sab or anyone else has tried? It is Possible using an API key to control the daemon, so to me its baffling. I have a firefox plugin for it but all it does is monitor i cannot add anything to my queue with it. A Firefox addon would be perfect use the APu key and have a small extension that is a small window that just has the add file option and the queue monitor/editor and bam! Although ideas are easy getting them to come into fruition, well thats something different all together or else i would have done it, LOL. 

Anyway my post is becoming very bloated for an update so lastly.

Should I Ask this question in a different Forum Category that might get more traffic from someone that knows Hella or would that just be a double post and bother everyone more? 
  
I am not going to spam this board (on purpose)

In all I am Surviving But i Feel i am half way there still Right now until I get a reply about HellaNzb Ill be working on how to make my .NZB downloads load directly into Sab currently it wants to do it with Lotta and since it doesn't work so i will have to change that. but i have found a how to here: [http://www.usenetshack.com/make-sabnzbd-default-program-open-nzbs-automatically/](http://www.usenetshack.com/make-sabnzbd-default-program-open-nzbs-automatically/)
Its probably easier than the above link says  to do ( i have yet to read it all and check if it even relevant) Although its all i have right now I will look until i find it.

I hope it works Thanks again for those who have read this even if they could not help i know someone out their will know i just need his/her attention is all. Also He/She has the time to help of course so if you can ask your friends LOL.

[CENTER]_**THANK YOU ALL**_
[/CENTER]

---

### Post by new_tolinux on 2010-04-13
> **BeatnikBandit said:**
> Ill be working on how to make my .NZB downloads load directly into Sab currently it wants to do it with Lotta and since it doesn't work so i will have to change that.

I guess you did find the option to monitor a specified folder for .nzb-files and "scan" that folder every "x amount of time". That's the option I use for it, and it works great.
It's my "main" download-directory, and it also handles "non-nzb-files" in that folder perfectly (it doesn't do something with them, only takes out the .nzb-files and load them into the queue).

---

### Post by BeatnikBandit on 2010-04-13
That is exactly what i had to do for sab to auto download thank you new_tolinux! BTW that was Fast Thank you for that too!

Now i think i have figured out my Hella Issue. When i run lotta it says it cant write to the directory because it was created with root (IDK why but Hella set it up that way and since i wa in sudo while i installed it and the conf is a protected file this is what i think my issue is) now I think that is my only issue.

So i have a new question:

So how do i install hella to work? i could run everything via sudo i think but thats not what i want. I think if i need to create the directory's on my user account and configure hellas conf file to point to them so lotta gets access. Since hella conf file is protected i must use sudo/root to edit it and in the process i believe it created the directory's so I think this is my issue and i don't exactly know how to do that as i don't even know the folders it will create and i must make them EXACT for it to work. I think the real fix is to somehow give my user account access to all things HellaNZB?

Anyone that knows anything about such things I would appreciate your help. 
I am still not giving up on it even though Sab isqworking flawlessly i am now just becoming obsessed and in the process i will learn so i want to do it. 

again thank you to every one who replies and anyone who even reads this thinking they may be able to help io appreciate everything. TIA.

---

### Post by new_tolinux on 2010-04-13
If it is a rights-issue, you always could try to chmod/chown the folders.
For this example I assume your download-folder is ~/.hellanzb/downloads (that's the same as /home/yourusername/.hellanzb/downloads)
If it isn't, replace it by the correct folder.

```

sudo chown -R yourusername:yourgroupname ~/.hellanzb/downloads
sudo chmod -R 770 ~/.hellanzb/downloads
```
What it does:
chown -> sets your username + usergroup as the owner of the folder and its subfolders.
chmod -> grants read+write+execute to your username + usergroup to the folder and its subfolders, but also grants "no access" to the-rest-of-the-world.

---

### Post by BeatnikBandit on 2010-04-14
Firstly new_tolinux, its time to change your name to something different LOL

Well My system just locked up after typing a long post so you guys are lucky i don't have the gas to retype it all so here is the jest.

First i think its a rights issue because the gui could connect with the daemon but could not read or right from the folders then i noticed in my home directory i had a new directory that was root owned /home/myusername/incomming. So Now i know i need to make the directory in the conf file to start in my home directory not from the bottom of the file system up. One thing i don't understand is the conf file is root access I understand that as it should be protected but then why would it create root directory's so i HOPE it will fix the issue after i fix the conf and directory's and with my limited knowledge at troubleshooting and the immense help i have receive I will do all i can and report back. This may take me a couple days as i have put this on the back-burner since installing Sabnzb+.

I will play with it more now that i have more knowledge on it so i hope it will work eventually.

Now i wanted to ask a simple question that i will be looking for soon but i thought i would just tack it on here in the hopes for a easy answer. first of all i am running ubuntu on a laptop (my first complete Ubuntu laptop install and on a DELL I am extatic everything worked with no tweaking even my pcmcia wifi card as this computer is that old.) So what i want to do is Completly Disable my Touchpad as i hate them I never could use them with the ease a mouse provides, I have been using laptops exclusively for about 5 years now and i NEVER used it although every other laptop i had there was some way to disable it with a button to do it, well this laptop does not have that option so its software only for this and i will Never use it again either so i believe i have talked enough about it as i might even figure it out before i get an answer LOL

I am still Determined to get HellaNZb to work Right now i don't even care if i end up not liking it i simply must conquer it and learn in the process. there is no better way to learn IMO.


[CENTER]**_As Always I Thank You All So Much for Helping me I Really Appreciate it_**
You Guys/Gals Rock :guitar:
[/CENTER]

---

### Post by new_tolinux on 2010-04-14
Firstly I have thought about changing my name and I decided not to do it in the near future.
As there are some things that I think I understand about "linux", but there's lots and lots of things I don't know and I do still post questions in the "Absolute Beginner Talk"-section of this forum.

I guess it's a security-measure to have the config-file root-only write-access, but that would require hellanzb to run as root if you want to change the config through the GUI.
That a program with root-access does create directories as root is not that hard to understand. As mentioned in my post above you'll just have to chown and chmod it. You can quite securely do so, as root can't be denied access (so even if the program is running, it can access that folder).

I recently had a thread about starting sabnzbd and a few other things. That because I don't want _any_ download-tool to run as root. Maybe it's of some use for you too ([link](http://ubuntuforums.org/showthread.php?t=1451187))
When you start hellanzb as a normal user, it shouldn't create root-only folders either. Although you might have re-assign rights to the current folders (or delete them and have them made again).

About the touchpad: maybe [this thread](http://ubuntuforums.org/showthread.php?t=205594) can be of use.

---

### Post by mister_p_1998 on 2010-04-14
I would persevere with Hellanzb, I use it totally automated & it works like a dream. I installed it, put my username/password in the conf file along with my usenet server (easynews) and it starts at 00:30 every weekday in cron, getting killed at 18:00 weekdays by Cron. Lottanzb detects a running copy of Hella, so theres nothing to setup. As long as Hella is running with a valid usenet server (eg news.easynews.com) and a valid username/account for that server it works great. I have another great program called Leechr scan NZB sites for stuff I want, and it downloads them straight into Hellanzb's inbox, where it downloads them, unpacks them and puts them in the 'Done' folder which I have a shortcut to on my desktop. I get up in the morning and all my new downloads are waiting for me! I would stress you probably need a premium usenet account as the free noes wont have all the parts of big downloads.
Steve

---

### Post by cb951303 on 2010-04-14
I don't see your problem.
install lottanzb and run it. that simple.

PS: I do all my usenet download with PAN. it's far less intuitive but much more stable. lottanzb is always unbearably buggy for me (or maybe hellanzb is)

---

### Post by BeatnikBandit on 2010-04-15
mister_p_1998 (steve) it sounds like you know how to get this going! from the sounds of it i must have just made an incorrect conf file?

I do use a premium server and recommend it to anyone who uses the usenet for downloading at all I am currently using Astraweb and am paying $11 a month.

Now for my question Currently I am using Sabnzb+ although i still have this want to get hellaNZB working because i haven't been able to do it. Could you do me a Big favour (BIG for me hopefully not for your) and possibly make me a config file?

here is my information again for ease of use i know its a repost but i want to make it easy for you if at all possible. (i normally use SSL but in this case i am not worried i more want it to just work)

[LIST]
[*] Server Address: us.news.astraweb.com:119
[/LIST]

[LIST]
[*] For username and password could you just put "username" and "password" in all areas its needed?
[/LIST]

[LIST]
[*] For Downloaded Files could they go to a folder in my home directory called /incomming/
[/LIST]

[LIST]
[*] My username for ubuntu is matthew
[/LIST]

[LIST]
[*] I would like to use 7 connections
[/LIST]

[LIST]
[*] My download speed is 20 mbits or 2 MB a sec
[/LIST]

[LIST]
[*] If you can i would love it to start at 5:00 and shut down at 18:00
[/LIST]
 PLEASE tell me if you need anything else or don't understand the way i typed this. I would SOOO appreciate it if you could help me with this you couldn't know! I would love you. (as a brother!:))

Basically the way you have your system set up it is exactly what i would like I would prefer Please tell me if you can do this for me as far as i know all i would have to do is plug in the conf file you make for me and it should work like a dream? am i correct?

you don't know how much i have been waiting for someone like you to help me with such a thing as so far almost everyone i talk to does not know hellanzb they are just trying to help me. Your post made me Very excited I hope you can help me and I hope you want to! 

I am just such a newb IDK what i can do if you want you can PM me and i can invite you to Google Voice, Newzbin.com, or Google Wave, other than that i don't know what i can provide for you in appreciation of helping me. Personally out of the above I get the most use out of Google Voice its great and since newzbin got sued they no longer have the content i want so i have started using nzbmatrix i think its better right now and i like that it is a lifetime membership instead of 50 cents US a week (the site is based on english currency so its 25 pence a week with a minimum of 2 pounds per "account, top up" 

[CENTER]-------------------------------------------------------------------------------------------------
[/CENTER]

This part is to reply to cb951303:

lotta can be run in several ways, it can run on its own without hella but all it does is download without hellaNZB it does not post process the compressed file and if needed repair with parity files, then it also can be a gui front end for HelllaNZB and then you get all your extra options.

Now for Pan I have used it for years for basic small file downloading and browsing, I think if the developers of the program first add NZB support and then just add an auto-rar to it like a windows application i know called newsbinpro it would be a contender but as of now IMO its just NOT up with the times right now EVERYONE uses NZB files and it needs to be implemented in pan then it would be great especially since its been ported into OSX and Windows under the GHU license it would be VERY popular. This is my Opinion of Pan I still use it for reading posts, posting replies but i only use it to download single files that NZB's are not needed for since i know where they are and i follow the Groups. So simply like i said Pan is Great but IMO behind the times and needs some fast development ASAP to be a contender! LOL

---

### Post by mister_p_1998 on 2010-04-16
Ok heres your hellanzb.conf file,rename it from hellanzb.conf.txt to hellanzb.conf,  you need to rename it to hellanzb.conf (take the .txt off) it needs to be copied to /usr/etc (you need to be root to do this) 
make sure you are in the same dir as hellanzb.conf and type: sudo cp hellanzb.conf /usr/etc/

Take note of the following line, this shows where Hellanzb should place its working folders:

# Important locations
Hellanzb.PREFIX_DIR = '/home/steve/hellanzb'
or where ever you want it to go (/home/matthew/hellanzb)

When you're happy with the setup, type hellanzb in a commandline, you should see the following pic

to start downloading, drop your NZB files into your /home/matthew/hellanzb/nzb/daemon.queue/

When theyre finished, they should be moved to the done folder


to autostart you need to get to get to grips with cron, we'll sort that out later.

---

### Post by cb951303 on 2010-04-16
> **BeatnikBandit said:**
> 
lotta can be run in several ways, it can run on its own without hella but all it does is download without hellaNZB it does not post process the compressed file and if needed repair with parity files, then it also can be a gui front end for HelllaNZB and then you get all your extra options.

Now for Pan I have used it for years for basic small file downloading and browsing, I think if the developers of the program first add NZB support and then just add an auto-rar to it like a windows application i know called newsbinpro it would be a contender but as of now IMO its just NOT up with the times right now EVERYONE uses NZB files and it needs to be implemented in pan then it would be great especially since its been ported into OSX and Windows under the GHU license it would be VERY popular. This is my Opinion of Pan I still use it for reading posts, posting replies but i only use it to download single files that NZB's are not needed for since i know where they are and i follow the Groups. So simply like i said Pan is Great but IMO behind the times and needs some fast development ASAP to be a contender! LOL

AFAIK lottanzb *only* works with hellanzb but gives you couple of choice about how to use it.
It can either use hellanzb as a system-wide service that runs everytime, or it can run it everytime you start a download and then quit when the download finishes.

BTW, PAN supports NZB files, since I'm using it for more than 3 years now I'm pretty sure it's not newly supported.

---

### Post by mister_p_1998 on 2010-04-16
How do you run it when you start a download?
I have it start at midnight on cron, then it gets killed at 18:00, it watches the inbox for NBZ's placed there by leechr.

Steve

---

### Post by BeatnikBandit on 2010-04-16
**_Wow two more replies and good ones too!!_**

mister_p_1998: 
Thank you soo soo much for giving me a HellaNZB conf file that i know works and I should be able to understand! (for some reason I think the multiple server setting part messed me up and also the directory setting) So now that you have provided me with one that you know works, If i cant get it to work then we know its human error and that can be fixed easily, I hope. 

I will try to get it working and report back with any changes i have made and weather or not it works. I will be running it Pretty much the exact way I run Sab as i manually run and shut it down. 
Also I have been told its not a good idea to leave these programs/daemons running when you shut down without shutting them down first so I may ask you for a lesson soon to automate it. 

(that is only if it doesn't bother you) I will ask first and if i am too dense to get it then i understand if you want me to learn more on my own before more lessons we all need a LITTLE homework no matter how much we hate it LOL. 
> 
Rant:
(I graduated over 10 years ago) should be 8 but i graduated high school early, not bragging i went to a charter high school so i could work and finish school faster, and still doing homework weather it be College, yes i am in my 6th year but i work and am part time or life its always good to learn. Personally I Love to learn and although practice doesn't make perfect (only because i believe humans are not perfect therefore cannot create anything Perfect as there is always some way of making anything better) so I think nothing can be prefect but if its the best you can do that is as much as you can strive for. If you try to be perfect you will go insane just ALWAYS do your BEST and as long as you do you will learn and get better every time. Sorry for the rant. :([CENTER]________________________________________________________
[/CENTER]

cb951303: 
Thank you for informing me more about Pan!!! I used it for years but i stopped during what i know now was a short period when it did not support NZB files I have version .133 and ya know what. when i just opened it to check the version i clicked file and the FIRST OPTION is NZB. I have no problem with admitting i was wrong and i was wrong. 

I am sorry to everyone for providing incorrect information that's no good for anyone. THANK you for correcting me! 

Does it just download NZB files Like Klibido (i bet faster if it does KLlibido is terrible IMO) or does it also process them. 

Pan has been around for a while. Before .NZB files it was my sole Usenet Client even in windows. (that's probably the best thing about it, it is a GUI that has a port for windows Linux and OSX its FREE it supports NZB files. I will recommend it to anyone new at the Usenet since i think its the best program that supports nzb files for new users!

That's just GREAT to Know that it supports Nzb files Ill have to try it out now I already use it just not for nzb. When i try it out it will be to check the speed and one to see if it has post download processing. 

The ONE problem i have with it that maybe you know how to fix is that the Max connections allowed when setting up a server (afaik) is only 4 I get about 3/4 my max speed with 4 connections i need at least 6 i prefer 6-8 as more adds system load and less does not max out my speed of 2mbits. Is their a way around the max connections of 4 per server?

[CENTER]_________________________________________________________
[/CENTER]

As always Thank you all for posting and even just reading this thread as it has been a long process but good things come to those who wait although i didn't have to wait long thanks to the great people on this board i think i am on my way to getting it all up and going!!

---

### Post by cb951303 on 2010-04-16
> **BeatnikBandit said:**
> 
cb951303: 
Thank you for informing me more about Pan!!! I used it for years but i stopped during what i know now was a short period when it did not support NZB files I have version .133 and ya know what. when i just opened it to check the version i clicked file and the FIRST OPTION is NZB. I have no problem with admitting i was wrong and i was wrong. 

I am sorry to everyone for providing incorrect information that's no good for anyone. THANK you for correcting me! 

Does it just download NZB files Like Klibido (i bet faster if it does KLlibido is terrible IMO) or does it also process them.

by processing if you mean does it decode yENC or uuencodethen yes but it doesn't do auto unrar which I think not that important and very annoying for some people like me :) 

> 

The ONE problem i have with it that maybe you know how to fix is that the Max connections allowed when setting up a server (afaik) is only 4 I get about 3/4 my max speed with 4 connections i need at least 6 i prefer 6-8 as more adds system load and less does not max out my speed of 2mbits. Is their a way around the max connections of 4 per server?


I believe that's a bug. since I can max the speed with 4 connections it didn't bother me before but that may be a problem for other people. AFAIK there is no workaround.

---

### Post by BeatnikBandit on 2010-04-17
I was busy yesterday so i have just begun to get at working with this. i have gotten your conf file I appreciate helping me with the config, on my conf file i messed up the sever part as i didn't understand it as i suppose the first like is the name of the server and the second is the actual server IDK but anyway the only changes i name was changing the home directory and i am wondering about the max speed option?

I changed this line
```

# Important locations
Hellanzb.PREFIX_DIR = '/home/matthew/hellanzb'

```I don't understand this line, It looks to me that its about speed limiting and i dont want that at all, since it says # limit to 150kB/s it makes me think i should change it do i need to? as i said my max speed is 20 mbits so i want to get what i pay for ya know.
```

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s

```Other than this i am now going to go and play with it and see what happens.
Thank you soo much with helping me set this up!!

---

### Post by mister_p_1998 on 2010-04-17
> **BeatnikBandit said:**
> I was busy yesterday so i have just begun to get at working with this. i have gotten your conf file I appreciate helping me with the config, on my conf file i messed up the sever part as i didn't understand it as i suppose the first like is the name of the server and the second is the actual server IDK but anyway the only changes i name was changing the home directory and i am wondering about the max speed option?

I changed this line
```

# Important locations
Hellanzb.PREFIX_DIR = '/home/matthew/hellanzb'

```I don't understand this line, It looks to me that its about speed limiting and i dont want that at all, since it says # limit to 150kB/s it makes me think i should change it do i need to? as i said my max speed is 20 mbits so i want to get what i pay for ya know.
```

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s

```Other than this i am now going to go and play with it and see what happens.
Thank you soo much with helping me set this up!!

Like I said # disables the function, so leave it as is, your speed will run at the max of your connection/News Server
BTW I set your number of connections to 7 as requested.

Steve

---

### Post by BeatnikBandit on 2010-04-23
Well thanks to mister_p_1998 I have gotten everything working seamlessly all my problem was a incorrectly configured Conf file WTF I know what a long post for that. well i am not going to mark it solved yet as i still need help. (you want to kill me yet LOL please dont) If mister_p_1998 obliges then there will be more learning to happen about automating the program. 

First i want to know how to set it to Startup and ShutDown on its own by the use of Cron, something i know nothing about.

Lastly I want to try and automate my downloads using certain websites RSS feeds as i know it is possible somehow but how I have no idea! I hope its possible with HellaNZB

As of now It kicks butt I use it with LottaNZB currently and it kicks the butt out of SabNzbd+ and although i still use pan personally i prefer the auto rar/par that HellaNzb Provides.

Right now i am pretty happy with a lot of thanks to mister_p_1998 I think he gets a :KS for the week LOL anyway thanks for everything you have done for me so far man you kick A$$ (thank you for it not being mine) you are a great guy its hard to put up with me and  Mister P seams to be able to handle it.
[LEFT]
[/LEFT]
[CENTER]THANKS THANKS THANKS
[/CENTER]

---

### Post by mister_p_1998 on 2010-04-24
Let me know how you get on with that cron stuff I sent you.
Steve

---

### Post by nhasian on 2010-04-24
great!  then you'll be pleased to learn that LottaNZB is [dropping hellanzb as a backend in favor of SABnzbd+]("http://www.lottanzb.org/category/news/") hehehe

course i'm not quite sure why you would need a front end for SABnzbd+ can't you access it from any web browser?

> **BeatnikBandit said:**
> Well thanks to mister_p_1998 I have gotten everything working seamlessly

---

### Post by cb951303 on 2010-04-25
considering that latest hellanzb stable release was on march 2007 I say good for them. I will give it another chance when it starts using sabnzbd

---

