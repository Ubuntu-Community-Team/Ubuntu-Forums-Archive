---
title: "Streaming 1080p Video within a LAN(Help)"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Layvian on 2011-01-22
[SIZE=3][COLOR=Blue]ANSWER TO THREAD SOLVED BY: SANDYD

HOW-TO[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]

OPTION: Web Server[/COLOR][/SIZE] [SIZE=3][COLOR=Blue]
METHOD: Apache2 Install

_Explanation_  [/COLOR][/SIZE][SIZE=3][COLOR=Blue]: 
Using Apache2 You are able to place all videos in the "/var/www" folder and play them on the LAN via VLC Media Player.

_Step(s)_  [/COLOR][/SIZE][SIZE=3][COLOR=Blue]:
[/COLOR][/SIZE] 
[LIST=1]
[*][SIZE=3][COLOR=Blue]Install VLC Media Player(via Ubuntu Software Center)[/COLOR][/SIZE]
[*][SIZE=3][COLOR=Blue]Install Apache2 and allow the "/var/www" folder to be used.[/COLOR][/SIZE]
[LIST]
[*][SIZE=3][COLOR=Blue]```
sudo apt-get install apache2
gksu nautilus /var/www
```[/COLOR][/SIZE]
[/LIST]
 
[*][SIZE=3][COLOR=Blue]Move Video content to "/var/www" folder.[/COLOR][/SIZE]
[*][SIZE=3][COLOR=Blue]Open VLC on Second Computer[/COLOR][/SIZE]
[*][SIZE=3][COLOR=Blue]Click on Media > Advanced File Open.. > Network [Tab][/COLOR][/SIZE]
[*][SIZE=3][COLOR=Blue]Enter Video Host IP with movie file(ex. 192.168.1.2/Valkyrie.mkv)[/COLOR][/SIZE]
[*][SIZE=3][COLOR=Blue]Click Play and Enjoy[/COLOR][/SIZE]
[/LIST]
 ===============================================================================
====ORIGINAL====
===============================================================================
I have a number of 1080p .mkv files on my main Desktop of which is running Ubuntu.  I have been trying to stream a video via VLC, and am able to stream it but it is very laggy, to the point it is unwatchable.

Normal Playback on VLC is fantastic on the computer, but it seems to give up with a stream.

Here is what I have done so far:

_First Attempt_:

[LIST=1]
[*]Turned on VLC Media Player
[*]Media > Advanced Open File..
[*]Add.. - Select Media File
[*]Click "Down Arrow" next to play and choose "Stream"
[*]Click Next ("Source:", and "Type:" are Correct)
[*]Under "Destinations" I choose "New Destination" - UDP @ port 1234 with my IP Address set to the IP of the receiving computer.
[*]Clicked "Display locally"
[*]Left "Active Transcoding" Checked
[*]Clicked Stream
[/LIST]
_Result_:
Video once opened from the opposite computer did not play, or was extremely latent.

_Second Attempt_:

[LIST=1]
[*]Same [1 - 5] Previous Attempt
[*]Under "Destinations" I choose "New Destination" - rtp @ port 5004 with my IP Address set to the IP of the receiving computer.
[*]Same [7 - 9] Previous Attempt
[/LIST]
_Result_:
Playback and Stream on Second computer worked but was very latent, and stopped.

_Last Attempt_:
I performed the same as "Second Attempt" but this time I changed Caching to 2000ms, and the video was a little better, but then finally stopped again.

Does anyone know how to fix this?  If not has anyone gotten 1080p streaming to work by another application?  Or used another method?  Any help would be awesome.  I will continue to try different methods myself, and post if any of them work.

Thanks,

Layvian

---

### Post by sandyd on 2011-01-22
> **Layvian said:**
> I have a number of 1080p .mkv files on my main Desktop of which is running Ubuntu.  I have been trying to stream a video via VLC, and am able to stream it but it is very laggy, to the point it is unwatchable.

Normal Playback on VLC is fantastic on the computer, but it seems to give up with a stream.

Here is what I have done so far:

_First Attempt_:

[LIST=1]
[*]Turned on VLC Media Player
[*]Media > Advanced Open File..
[*]Add.. - Select Media File
[*]Click "Down Arrow" next to play and choose "Stream"
[*]Click Next ("Source:", and "Type:" are Correct)
[*]Under "Destinations" I choose "New Destination" - UDP @ port 1234 with my IP Address set to the IP of the receiving computer.
[*]Clicked "Display locally"
[*]Left "Active Transcoding" Checked
[*]Clicked Stream
[/LIST]
_Result_:
Video once opened from the opposite computer did not play, or was extremely latent.

_Second Attempt_:

[LIST=1]
[*]Same [1 - 5] Previous Attempt
[*]Under "Destinations" I choose "New Destination" - rtp @ port 5004 with my IP Address set to the IP of the receiving computer.
[*]Same [7 - 9] Previous Attempt
[/LIST]
_Result_:
Playback and Stream on Second computer worked but was very latent, and stopped.

_Last Attempt_:
I performed the same as "Second Attempt" but this time I changed Caching to 2000ms, and the video was a little better, but then finally stopped again.

Does anyone know how to fix this?  If not has anyone gotten 1080p streaming to work by another application?  Or used another method?  Any help would be awesome.  I will continue to try different methods myself, and post if any of them work.

Thanks,

Layvian
Easy method.

Don't stream.

Set up a webserver, and set it up to host the file.
Then point vlc to the url of the file when you want to play it

---

### Post by Layvian on 2011-01-22
> **sandyd said:**
> Easy method.

Don't stream.

Set up a webserver, and set it up to host the file.
Then point vlc to the url of the file when you want to play it


Would I be able to do this without having another Computer to setup a server on?

---

### Post by BugBuster on 2011-01-22
Also try increasing the buffer size(network cache)!......Oops..please ignore!;)

---

### Post by Layvian on 2011-01-22
> **BugBuster said:**
> Also try increasing the buffer size(network cache)!......Oops..please ignore!;)


How High? I set it to 5000 and it was semi ok.

Update: I set it to 10,000 and it doesnt work at all. Sadly.  Sometimes the video doesnt even work and its just the auto now.  Maybe I and putting the number in the wrong cache area?!?!?

---

### Post by sandyd on 2011-01-22
> **Layvian said:**
> Would I be able to do this without having another Computer to setup a server on?
yes.
do this
```

sudo apt-get install apache2
gksu nautilus /var/www

```place stuff in there, delete whats already in the folder, then go to
```

http://ip-address-of-your-computer/
```

---

### Post by Layvian on 2011-01-22
> **sandyd said:**
> yes.
do this
```

sudo apt-get install apache2
gksudo nautilus /var/www

```place stuff in there, delete whats already in the folder, then go to
```

http://ip-address-of-your-computer/
```

I get this:

```
layvian@layvian-home:~$ gksudo nautilus /var/www
Initializing nautilus-gdu extension

** (nautilus:32628): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '32628'

(nautilus:32628): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


```

---

### Post by sandyd on 2011-01-22
> **Layvian said:**
> I get this:

```
layvian@layvian-home:~$ gksudo nautilus /var/www
Initializing nautilus-gdu extension

** (nautilus:32628): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '32628'

(nautilus:32628): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


```
typo. fixed.

---

### Post by Layvian on 2011-01-22
> **sandyd said:**
> typo. fixed.


Hey Sandyd, works fantasic, it might not be Streaming, but the long distance potential for this is greater.  Also I have issues with wireless none latent video playback using this, but I am sure I can play with it or lower it to a rate of 720p.


Thanks for all your help and patience.  I will be marking  this as Solved.


[SIZE=6]PLEASE NOTE THE ANSWER FOR STREAMING HAS NOT AND WILL NOT BE GIVEN ON THIS FORUM POST![/SIZE] [SIZE=6] ANOTHER ROUTE WAS TAKEN.[/SIZE]

---

