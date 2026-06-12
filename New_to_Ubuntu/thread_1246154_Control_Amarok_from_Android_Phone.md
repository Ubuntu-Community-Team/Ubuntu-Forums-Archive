---
title: "Control Amarok from Android Phone"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-08-21
Hi

I am the proud owner of a HTC Magic running Google's Android Mobile OS.

I am trying to figure out a way to control Amarok from my Android phone.

So, far I have found this: [http://jsharkey.org/blog/2008/08/20/amarok-14-remote-in-android-using-dcoppython/](http://jsharkey.org/blog/2008/08/20/amarok-14-remote-in-android-using-dcoppython/)

But, I'm not sure how to set it up. Any help would be appreciated.

If anyone knows of a better way to control Amarok from my Android phone, I would appreciate the suggestions.

Thanks!

---

### Post by SeanHodges on 2009-08-21
Hey,

I've been working on a project exactly for this purpose. It's not officially released yet as I'm preparing it for a competition, but an early release of the app can be downloaded and installed directly onto your phone (let me know if you don't know how to do this already).

You can get it from here:

[http://tesla.seanhodges.co.uk](http://tesla.seanhodges.co.uk)


It requires that you install an SSH server on your machine, but that should be all you need. If you decide to have a play with it, please let me know how you get on. :)


Cheers,

Sean

---

### Post by abhiroopb on 2009-08-21
Hi

The app looks incredible. Unfortunately, I get the following error when trying to install Tesla-0.2.apk:

"Tesla could not be installed on this phone"

---

### Post by abhiroopb on 2009-08-21
Hi

The app looks incredible. Unfortunately, I get the following error when trying to install Tesla-0.2.apk:

"Tesla could not be installed on this phone"

(Note: I have HTC Magic running cupcake)

---

### Post by SeanHodges on 2009-08-21
Hmm, it should work regardless of the phone...

The app is not signed and released on the Android Market yet, your phone may not have "allow unknown sources" enabled, try the following:

1) Go to the Settings
2) Click on the "Applications" menu
3) Tick the "Unknown sources" checkbox

If that doesn't resolve it, I may need to do something to the build to make it work for you. Let me know how you get on and I'll look into a fix over this weekend if it still does not work.

---

### Post by abhiroopb on 2009-08-21
Yes I have done that already actually. In fact I have installed numerous apps that I downloaded (e.g. FacebookSync and the full version of SipDroid).

This is the first time I've got the error actually.

Thanks a lot for all the help!

---

### Post by SeanHodges on 2009-08-21
I hit the same issue that you did when I tried to deploy the APK on my G1, turns out I did need to sign the application before it can be installed on other devices.

I've built a new APK with a self-signed certificate. It seems to install fine now. Feel free to go to that download site and get it. Let me know if it still doesn't work.

One thing worth mentioning; it currently only works with Amarok 2.0 or later. I haven't got around to supporting 1.4 yet. Let me know if you are using Amarok 1.4 and I'll look into adding support for it.

---

### Post by abhiroopb on 2009-08-21
Ah that last point would be a problem! 

I didn't really like Amarok 2.0's interface so I started using Amarok 1.4 again.

I'll try installing the App anyway and let you know if it installs.

Do let me know if you end up adding support for 1.4!

Thanks again.

---

### Post by abhiroopb on 2009-08-21
The app installed fine...and I also installed "openssh-server".

Is there anything else I need to do?

When I try connecting from my phone I get the following errors:

"Error whilst connecting to device: Failed to connect to SSH server, is it running?"

"Error whilst connecting to device: Host is not reachable"

In the Host section I am putting in the IP address that my router has assigned to my Laptop (19.168.0.101).

I have left the username and password blank.

---

### Post by abhiroopb on 2009-08-21
I also tried it with VLC...as this is something I'd like to be able to control from my phone as well!

---

### Post by SeanHodges on 2009-08-21
Well a blank username and password won't help, as the phone needs to connect to your running desktop session over Wifi. You need to enter the username and password for your PC so it can connect remotely.

Having said that, the error message your getting suggests that it cannot even ping your computer. Can you confirm that Wifi is enabled on your phone, and successfully connected to your router's network? This can sometimes be the tricky bit, as connection problems can be a bit difficult to diagnose.

It sounds like you have set everything up right, openssh-server is the only dependency you should need. If we can crack what's causing this connection problem, it'll definitely help me to improve the process... Thanks for giving it a try!

---

### Post by abhiroopb on 2009-08-21
Ok...I was being really stupid. I put in my username and password and CORRECTED my IP (I was putting in 192.168.0.101 instead of 192.168.1.101).

I started openssh as well by doing: "sudo /etc/init.d/ssh start".

So, I connected fine.

Now I'm getting the following error (from connection to VLC and Amarok):


Could not send command to device: dbus-send --session --print-reply --dest=org.mpris.vlc --type="method_call" /Player org.freedesktop.MediaPlayer.Pause :- Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.mpris.vlc was not provided by any .service files
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.mpris.vlc was not provided by any .service files

---

### Post by SeanHodges on 2009-08-21
Aha, now I've had this before. It should only be a problem for VLC (and I suspect Amarok consequently isn't working because you are running 1.4).

Basically, VLC won't allow you to remote control it until you add a switch to turn it on. These steps should fix that:

1) Right-click on your Applications menu and go to "Edit Menus"
2) Navigate into "Sound & Video" on the left panel
3) Right-click on VLC, and select Properties
4) Change the "Command" box so it reads as this:

```
vlc --control dbus %f
```

Restart VLC, and Tesla should work correctly after that. It's a really annoying problem, I plan to ask the VLC maintainer on Ubuntu if they can make that a default setting.

---

### Post by abhiroopb on 2009-08-21
Ok that worked perfectly :)!

Only problem is that I assume when vlc is updated this will be erased and I'll have to add the "control dbus" again.

Anyway, again great app. I find that most open source apps are great functionall, but not the best designed. I am in love with Tesla's simple interface!

A couple of suggestions (at least for VLC):
1. Something to show the name of the video playing.
2. Bar displaying how much of the video has been played (I think its called a "seek" bar). This would also be useful to fast-forward and rewind the video.
3. A master volume control would be useful (instead of the volume control for just the app).

Otherwise the app is perfect!

Great job.

---

### Post by abhiroopb on 2009-08-21
Also do let me know if you do add support for 1.4.

Thanks

---

### Post by SeanHodges on 2009-08-21
> **abhiroopb said:**
> Ok that worked perfectly :)!

Great! This has helped me with some ideas on improving the instructions as well.

> Only problem is that I assume when vlc is updated this will be erased and I'll have to add the "control dbus" again.

Yeah, it's not the ideal solution. I'll have a think about how I might circumvent this problem more permanently...

> 1. Something to show the name of the video playing.
2. Bar displaying how much of the video has been played (I think its called a "seek" bar). This would also be useful to fast-forward and rewind the video.
3. A master volume control would be useful (instead of the volume control for just the app).

All great suggestions. I'll put them on my TODO list, and I will try and get Amarok 1.4 support added this weekend (I will post on this thread so you know when it's available).

Thanks for your encouraging comments!

---

### Post by ptviperz on 2009-08-21
> **SeanHodges said:**
> Hey,

I've been working on a project exactly for this purpose. It's not officially released yet as I'm preparing it for a competition, but an early release of the app can be downloaded and installed directly onto your phone (let me know if you don't know how to do this already).

Hi Sean,

Can you provide instructions?

---

### Post by SeanHodges on 2009-08-21
I will write up some proper instructions soon, but for now if you follow these you should be able to get it working:

1) Follow my steps for enabling unknown sources here: [http://ubuntuforums.org/showpost.php?p=7823669&postcount=5](http://ubuntuforums.org/showpost.php?p=7823669&postcount=5). You can turn this setting back off after you have installed Tesla if you like.

2) Type the following URL into your Android Browser: [http://bit.ly/tesla0-3](http://bit.ly/tesla0-3)

3) Once the app is downloaded, open it and follow the on-screen instructions to install it.

4) You need to install OpenSSH on your PC so it can connect, click on this link to install it within Ubuntu: [apt://openssh-server]("apt://openssh-server")

5) Follow these steps if you want to use it with VLC: [http://ubuntuforums.org/showpost.php?p=7824159&postcount=13](http://ubuntuforums.org/showpost.php?p=7824159&postcount=13)

The username and password are the ones you use to log into your PC. I recommend using your IP address for the host, because I've had problems myself getting it to connect with the host name. Let me know how you get on. I plan to put this on the Android Market soon so installing and updating it will be easier.

---

### Post by abhiroopb on 2009-08-22
One other thing I'd like to add. I'm not sure if this is required, but I started openssh by doing: "sudo /etc/init.d/ssh start" on the PC.

---

### Post by SeanHodges on 2009-08-24
Hey abhiroopb,

I've released a new build with Amarok 1.4 support, you can download it from the Tesla project site, or directly [here]("http://bit.ly/tesla0-5"). You should be able to select "Amarok" and it will work out which version of Amarok you are running.

Please let me know if you encounter any issues, I'm using Amarok 2.1 over here, so between us we should catch any problems :)


ptviperz,

Please let me know if you get chance to try Tesla out, I could really use the feedback in the run-up to the Android developer challenge.

---

### Post by abhiroopb on 2009-08-24
Hi,

I installed the app and ran it fine.

When I launch VLC it launches fine. Whenever I launch the amarok app it gives me the following message:

"The application Tesla (process tesla.app) has stopped unexpectedly. Please try again."

---

### Post by SeanHodges on 2009-08-25
I can reproduce this when I'm not playing any music in Amarok when I connect. I think it is trying to pull the song information and crashing because the player is stopped.

I'll see if I can get a fix available by tomorrow, in the meantime a work-around is to ensure Amarok is playing before connecting to your PC from Tesla.

---

### Post by abhiroopb on 2009-08-25
Yup that fixed it fine! Works great. Really useful to be able to control my player from the phone.

A few comments/suggestions:

1. The volume control does not seem to do anything. As I suggested before it may be useful to integrate it with the main volume control (and not Amarok specific) as I usually keep amarok maxed out and I manually adjust the main volume.

2. The cover art and album information looks great on the phone. But I notice that it occasionally switches back to the "Demo" album (and blank cover art and then switches back to the Currently playing song.

3. Still randomly crashes (a lot!).

4. Would be useful if I could see the songs in the current playlist or search the database generally (I noticed that the playlist button is non-functional at this point).

But otherwise this is an immensely useful app! Well done!

---

### Post by SeanHodges on 2009-08-25
> **abhiroopb said:**
> 1. The volume control does not seem to do anything. As I suggested before it may be useful to integrate it with the main volume control (and not Amarok specific) as I usually keep amarok maxed out and I manually adjust the main volume.

Strange, it seems to work for me (within Amarok). I'll take a look at this as well.

I agree a master volume control would be a good addition. I think there will be people who want a master volume and others who will only want it to affect their player. 

I can see 2 ways this could be done - either have 2 volume controls on the app, or have a preference setting that switches the behaviour of the existing volume control. I'm leaning to the latter option, what do you think?

> 2. The cover art and album information looks great on the phone. But I notice that it occasionally switches back to the "Demo" album (and blank cover art and then switches back to the Currently playing song.

3. Still randomly crashes (a lot!).

I think these are both related to the Amarok 1.4 song retrieval bug you discovered earlier. I will look for a fix that stops the crashing, and hopefully resolves the blanking song info panel bug.

I'd be interested to know if you experience the force-closing with VLC as well, if so I might be on the wrong track.

> 4. Would be useful if I could see the songs in the current playlist or search the database generally (I noticed that the playlist button is non-functional at this point).

I hope this can be implemented fairly soon. It's going to need a bit of careful planning because most players don't expose their music collection database. I think it will need to be a simple playlist to start with, and then gradually add a collection browser feature to each media player configuration as ways to create them are discovered.

> But otherwise this is an immensely useful app! Well done!

Thanks! :)

---

### Post by abhiroopb on 2009-08-25
> **SeanHodges said:**
> Strange, it seems to work for me (within Amarok). I'll take a look at this as well.

I agree a master volume control would be a good addition. I think there will be people who want a master volume and others who will only want it to affect their player. 

I can see 2 ways this could be done - either have 2 volume controls on the app, or have a preference setting that switches the behaviour of the existing volume control. I'm leaning to the latter option, what do you think?



Not sure why it isn't working. Tried it a number of times...

I agree with the latter option. Otherwise it would get confusing. In fact having two is probably confusing anyway. Not sure how to get around it though. I assume you prefer having the application control the volume? Have you had a look at gmote? The app is similar in many ways, but it is more useful to PLAY music, than to CONTROL it, as it does not let you control the app itself.

I guess if you label it "Master Volume" and "Application Volume" it would be clear enough.

> 

I think these are both related to the Amarok 1.4 song retrieval bug you discovered earlier. I will look for a fix that stops the crashing, and hopefully resolves the blanking song info panel bug.

I'd be interested to know if you experience the force-closing with VLC as well, if so I might be on the wrong track.


I have not (as far as I recall) had a similar problem with VLC...seems to be related to Amarok. When I have a bit more time (later this week), I'll try it out on Rhythmbox and Banshee as well

> 
I hope this can be implemented fairly soon. It's going to need a bit of careful planning because most players don't expose their music collection database. I think it will need to be a simple playlist to start with, and then gradually add a collection browser feature to each media player configuration as ways to create them are discovered.


I totally understand. Have you had a look at "[amarok-remote]("http://code.google.com/p/amarok-remote/")"? It's not as slick as your app, actually its web based and you need to have something running on your computer as well. It seemed good in the beginning but it was far too buggy. But this allows you to search the currently playing playlist.

I am also using MySQL and NOT the default (which I believe is SQLite). Could this be causing any problems?


> 
Thanks! :)

You're most welcome.

May I ask which competition this is for? Are you working on your own?

---

### Post by abhiroopb on 2009-08-25
**UPDATE:** Just restarted my computer (by extension Amarok), my HTC (and by extension Tesla).

First test:
The volume control worked fine.
The album information (and cover) did not show up.
The play button and the seek buttons worked.
The app crashed after about 30s.

Second test:
Ditto the first, but this time album art was available
App crashed again after about 20s.

VLC works fine (with or without anything playing). But, there is a slight problem with the VLC volume control. VLC allows the volume to go up to 200%, so, I like to keep mine at about 150%...anyway Tesla only allows the volume to be set between 0% - 100%.

The only other feature I would suggest is the ability to fast forward and rewind (especially useful in VLC).

Thanks

---

### Post by abhiroopb on 2009-08-25
**Update 2:** Slight aesthetic quirk...If you pause the song in Amarok, the Play/Pause icon in Tesla does not change. But pressing the button works like normal...not really a major problem.

Another feature that might be useful is either a widget or some form of notification in the Androids notification bar.

---

### Post by SeanHodges on 2009-08-25
I believe I have fixed the force closing in Amarok 1.4, at least it doesn't seem to crash for me anymore. I've rolled a 0.6 release for you to try out:

[http://bit.ly/tesla0-6](http://bit.ly/tesla0-6)

> **abhiroopb said:**
> VLC works fine (with or without anything playing). But, there is a slight problem with the VLC volume control. VLC allows the volume to go up to 200%, so, I like to keep mine at about 150%...anyway Tesla only allows the volume to be set between 0% - 100%.

The only other feature I would suggest is the ability to fast forward and rewind (especially useful in VLC).

You raised a good point on the VLC volume, I've increased the threshold to 200% in the latest release. I've also added support for film title retrieval when using VLC. Let me know if you find any problems with the changes.

> Slight aesthetic quirk...If you pause the song in Amarok, the Play/Pause icon in Tesla does not change. But pressing the button works like normal...not really a major problem.

I thought someone would notice this sooner or later :) I have some code for handling the play/pause button in players that provide their playing status, but it proved to be a bit unstable (particularly in Amarok). I've turned it off for now, because as you say, it's not a major problem. But I do intend to re-visit the code at some point.

> Another feature that might be useful is either a widget or some form of notification in the Androids notification bar. 

Definitely, I think I'll look into the possibilities of widget/notification support once I've got the main application stable and working; but it's a good feature to keep in scope.

---

### Post by abhiroopb on 2009-08-26
The 0.6 update seems to have fixed the crashing problem. Also the volume for VLC and the filename update has been fixed.

Thanks for the update. Keep me posted on new developments please!

---

### Post by SeanHodges on 2009-08-26
Great!

Also in response to your question on which competition this is for; it's for the Android Developer Challenge ("ADC2"), and yes, right now I'm working on my own. (though the project is open-source, and I'm happy to accept contributions)

I'll be sure to post up any developments. Adding master volume control support and a seek bar are definitely planned for a near release, though my focus for the next couple of days will be on stability and UI clean-up to prepare for my competition submission.

---

### Post by abhiroopb on 2009-08-26
Good luck!

Glad to continue helping in any way I can!

---

### Post by SeanHodges on 2009-08-29
abhiroopb,

I've just released a new version of Tesla, in it, I've added support for changing the system volume instead of the media player one.

If you would like to download the latest release from here: [http://bit.ly/tesla0-7](http://bit.ly/tesla0-7), you should be able to switch the behaviour by pressing your Menu button, and selecting Preferences. The option is included in there.

Please let me know how you get on. I hope for this to be the last release candidate before I submit for this competition.

---

### Post by abhiroopb on 2009-08-30
Downloaded and installed.

Got a problem though:

Error Code 843110. I was attempting to adjust the volume in Amarok (NB: I had not changed between player volume and system volume, i.e. I had not touched the preferences).

The Album Information (and cover art) keep switching from the correct information to the "Tesla Demo" message (and blank cover art). This happens intermittently, but right now it seems to have fixed itself.

********************************

Changed the volume setting to "system volume".

The album information again is switching between the correct information and "Tesla - Remote Control".

When I try to change the volume the application crashes.

This might actually be a problem at my end.

I have had many problems with pulse and skype. So, I followed [this guide]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") to remove pulse from my computer.

Thanks

---

### Post by SeanHodges on 2009-08-30
> **abhiroopb said:**
> Downloaded and installed.

Got a problem though:

Error Code 843110. I was attempting to adjust the volume in Amarok (NB: I had not changed between player volume and system volume, i.e. I had not touched the preferences).

The Album Information (and cover art) keep switching from the correct information to the "Tesla Demo" message (and blank cover art). This happens intermittently, but right now it seems to have fixed itself.

********************************

Changed the volume setting to "system volume".

The album information again is switching between the correct information and "Tesla - Remote Control".

When I try to change the volume the application crashes.

This might actually be a problem at my end.

I have had many problems with pulse and skype. So, I followed [this guide]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") to remove pulse from my computer.

Thanks

Thanks for the feedback, I've been taking a look at the possible reasons for the issues you describe above, but I must admit it's a bit puzzling. The commands I'm using for the system volume are direct to ALSA, so it bypasses PulseAudio anyway. I have managed to reproduce the resetting album info area, but it's not immediately obvious what is triggering it.

I'll keep working on it, there must be some area of Tesla that is suseptable to high network latency or something similar. 

Be sure to let me know if you discover any other traits that might give us clues as to what's going on.

---

### Post by abhiroopb on 2009-08-31
Not sure about the audio at all. I played around with my sound settings. On amarok, in sound preferences, basically everywhere that had some vague option regarding sound.

Unfortunately, putting Pulse back is a bit of a headache for me so this is the only thing I am unable to try. If it is working on your system, then I assume that my playing around with the sound settings is the source of the problem (even though you say that Pulse is bypassed). 

The only thing I can suggest is if you follow the instructions in the guide (i.e. remove Pulse) and see what happens.

Thanks!

---

### Post by abhiroopb on 2009-09-01
Hi,

Just did a test of the VLC app.

I like the little "How To" to enable d-bus. Its really helpful...Sadly it does not work.

I followed it and enabled it, but even after restarting VLC I can't control it from Tesla.

I have to use the old method (highlighted by you before: [http://ubuntuforums.org/showpost.php?p=7824159&postcount=13](http://ubuntuforums.org/showpost.php?p=7824159&postcount=13)).

After this the control is fine. However, I noticed that while you changed the player volume to be raised up to 200% the percentages displayed in the Tesla volume app display only up to 100%. Again this isn't a bug as such, just a slight inconsistency.

Also, since this is the VLC app I understand that there is no reason to display album art. But the blank cover art is a little "dull"! I suggest changing it to the VLC logo. Another (slightly more difficult method) is to search for the movie "album cover" from IMDB. If for example I have labelled my video file as "Shawshank Redemption.avi" it should search IMDB and find the top hit and display the cover for that top hit.

The program Med's Movie Manager ([http://xmm.sourceforge.net/](http://xmm.sourceforge.net/)) has a similar type of feature that works quite well.

Again this is not something major, but the blank cover does not look very nice.

Other than these two points the VLC app works great!

Just as an update: the system volume change does not work whether I am using VLC or Amarok as my player on Tesla (although I didn't think this would be a problem in any case).

Hope this helps.

---

### Post by abhiroopb on 2009-09-01
Just found this app:

[http://code.google.com/p/android-vlc-remote/](http://code.google.com/p/android-vlc-remote/)

I prefer Tesla since it allows me to control both Amarok and VLC (one app is better than two). However, Android VLC remote's implementation of controlling VLC has a lot more useful features (e.g. ability to browse computer, seek bar, playlists, etc.).

Just thought it might be useful for you in developing Tesla.

---

### Post by abhiroopb on 2009-09-01
Sorry to flood you with posts but just noticed something.

Started up Tesla to control Amarok. All works fine (except system volume). But it took a full minute before the album information was displayed (usually it is instant). Further, like before it kept disappearing and reappearing.

---

### Post by SeanHodges on 2009-09-04
Thanks for all the info abhiroopb. I'll have a proper read of it this weekend, I have some fixes I'd like you to try as well so will post something up once I've got to that stage.

Have a good weekend :)

---

### Post by SeanHodges on 2009-09-05
abhiroopb,

I've rolled a test release for you to try. It's nothing exciting feature-wise - just the last release with some added improvements to the media info retrieval and system volume control handling.

If you wouldn't mind testing it and letting me know if it fixes your earlier issues, I'll apply the fixes to the next release, which I plan will have some new features thrown in as well.

You can download it from here: [http://bit.ly/tesla0-7-abhiroopb](http://bit.ly/tesla0-7-abhiroopb)

If the system volume is not fixed, could you post me the output of this command:

```
amixer
```


Good luck and thanks again :)

Sean

---

### Post by abhiroopb on 2009-09-05
hey there!

Just tried the new test release:

The album art seems to display fine as well as all the album information. 

Unfortunately, the system volume does not seem to be working (crashing like before):

and the display of amixer:
```

$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 18 [60%] [-19.50dB] [on]
  Front Right: Playback 18 [60%] [-19.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Mic Bypass',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'ExtMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]


```

---

### Post by SeanHodges on 2009-09-06
Looking at your mixer settings, I think I've discovered the problem. I've made the system volume code more flexible now.

Could you test this, see if it fixes your system volume control? [http://bit.ly/tesla0-7-abhiroopb2](http://bit.ly/tesla0-7-abhiroopb2)

---

### Post by abhiroopb on 2009-09-06
Works perfectly!! Thanks a lot!

Are my settings anomalous in any way? Or do you think the settings will apply to others as well?

---

### Post by SeanHodges on 2009-09-06
Glad to hear it's working properly at last. I hope to roll a proper release including those fixes soon.

I think your settings are fairly normal. There are just a few areas in my code where I had not allowed for the necessary differences between systems. I do test against 3 computers, but even that is not enough in some cases.

The media info bug was quite a common occurrence on wireless networks with a slower speed than my own. I needed to optimise some of the SSH connection code to allow for this.

The system volume issue was a tricky one. Each system has it's own set of sound channels and settings (e.g. most have a channel called "Master", some have one called "Front", others have neither, but have one called "PCM" - sometimes these are mono and other times stereo, etc).

I've made the system volume command check for these differences, and select the best match when getting/setting volume.

Your help has been extremely useful when tracking down these fixes, some people would have just given up and switched to something else :) Thanks for your patience. I'm looking at some of your other suggestions for inclusion in the next release, and I'll be sure to let you know when it's out.

---

### Post by abhiroopb on 2009-09-07
Hey...Yes it is a relief! Finally, I have something that controls amarok!

Arte you suggesting that mine might be slower? Of course I'm not sure what kind of gear you have...but I think my speeds are relatively stable. Although, it might be the fact that my laptop is quite old and does not support N, whereas my linksys router is a/b/g/n. But, since it isn't jumping around anymore...that discussion is purely academic anyway!

Yes I've had a lot of trouble with the various sound systems in Ubuntu. Difficult to figure out what is controlling what! And each player (i.e. VLC, amarok, skype, etc.) has its own set of options. I've posted this point in the brainstorm website. 

One problem I had...dunno if its a problem or a "feature". When I click on the "end call" button amarok would pause/play the song!

No problem! I'm glad to have helped. As you can tell I'm not the most savvy at programming. However, I have a keen interest in learning about software and I especially love testing new software. I did a lot of testing for the iPod with Banshee a while back. Its quite easy to do, I mean its really you and other developers that are doing all the hard work. Its not too much effort for me to say, "hey this isn't working, fix it!"


Also I really like you're app for a few reasons:
1. Only android app that controls amarok flawlessly (took a while but we got there - congrats!)

2. No need to have any "server" running on Ubuntu. A number of these remote apps (e.g. gmote) require that some sort of clunky java programme be running. All Tesla requires is the installation of openssh.

3. Its one app for both VLC and Amarok. However, I must qualify this point...The OTHER VLC remote programme I came across is far more useful right now as it supports the seek bar.

Good luck!

---

### Post by abhiroopb on 2009-09-09
Just updated and noticed the seek bar...useful addition!

Amarok:
Crashed when I tried to use it.

VLC:
Worked a few times and then crashed.

---

### Post by abhiroopb on 2009-09-09
Crashing on system volume change as well. Actually its crashing if I do most things. The 0.8 release seems VERY buggy for some reason.

---

### Post by SeanHodges on 2009-09-09
That is worrying. I've discovered a serious flaw in the query code that has become more problematic now we are communicating more data over the SSH connection (for the seek bar and "is playing" check).

Not sure how I missed it during my testing, one of those things I guess.

I'm going to roll a 0.9 release later tonight and cross my fingers that it fixes the issue. I'll be off on holiday tomorrow, so if you find it is still broken please drop me a message and I'll get back to fixing it as soon as I can.

Thanks for testing it. I hadn't got around to announcing the release so far, I'm glad I held off now!

---

### Post by SeanHodges on 2009-09-10
Well it took a little longer than I'd hoped, but I've rolled out a new release with a fix for the crashing issue. It should appear as version 0.8.1

I haven't seen any crashing since I applied the fix, please let me know if you have better luck with this release. I'll be on holiday for a week, but will be able to pick up any issues after then.


One thing I did notice during my testing is that there is a bug in VLC 0.9 (which is distributed with Ubuntu Jaunty), which means that the seek bar can seek up to ~2000 seconds worth of video before VLC resets the video back to the beginning.

According to [this commit report]("http://mailman.videolan.org/pipermail/vlc-devel/2009-May/060501.html") a fix was applied back in May, which means that it should be in the latest version of VLC (1.0.1). VLC 1.0.1 is also planned for distribution with Karmic in October. I haven't had time to investigate much further than that, sorry, but hopefully it will be possible to upgrade VLC on your machine and the seek bar will work correctly from then on.

---

### Post by abhiroopb on 2009-09-10
Hi there.

I updated Tesla to 0.8.1 and in the process of testing it out.

I have already been using VLC 1.0.1 for a while actually, so shouldn't be a problem for me, but unfortunately I can't test the older version.

One thing I do notice is that if you hold the phone in potrait mode the seek bar is difficult to control. Basically, its almost impossible to select a particular point in the film with any accuracy, especially if its a long film. For example, I'll try and move back 1 min and it goes back about 10! This isn't a technical fault, just that using your thumb to select is highly inaccurate. Perhaps adding a couple of buttons to allow "short jump" back and forward would help!

Thanks

---

### Post by abhiroopb on 2009-09-10
I got error code 83360 in VLC. But, I'm not sure if this actually caused a problem as everything else worked fine!

---

### Post by SeanHodges on 2009-09-10
Thanks for the feedback abhiroopb, definitely let me know if that VLC error is a recurring problem, and I'll take a look when I get back.

You have a point about the seek bar not being very precise. I'll consider including some jump buttons (or equivalent) in the next release.

---

### Post by abhiroopb on 2009-10-01
Hi,

Was wondering if there have been any updates to the app.

Cheers!

---

### Post by SeanHodges on 2009-10-01
Hi abhiroopb,

I didn't give you an update here, as I sent an email to the android-tesla-users mailing list and I noticed you were subscribed to it. If you're missing the email (sent Mon, 28th Sept) please let me know as there might be something wrong with the list.

Anyway, I did a release a couple of days ago, with some critical fixes for people having connection problems. I tried to rush out a few new features, but they really weren't stable enough so I left them out in the end.

I'm still working on the playlist support, it's been a bit tricky because each media player handles playlists differently. I sent some info on this to the [android-tesla-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=e4e95ff00909290131p4cc19249n13e4b1abf4358b4f%40mail.gmail.com&forum_name=android-tesla-devel") list. I think I'm making some good progress now, but there is still a little bit left to do before a release is possible.

I have managed to add Amarok 1.4 playlist support however, and some incomplete support for VLC and Amarok 2. I hope to roll a release soon with support for at least Amarok 1 & 2, VLC and Rhythmbox. Perhaps more players if time permits. 

I can build you another custom release with what I have so far, assuming you'll be happy to test it for me?

---

### Post by abhiroopb on 2009-10-01
Hi Sean,

I definitely didn't get that e-mail. I do remember signing up for it and even having RSS feeds for all your pages on the Tesla website, however, like I said I didn't get any updates. We can either continue conversing on this thread, or you could let me know where I should sign up and I could subscribe to RSS feeds for those pages as well to keep me in the loop.

I haven't reall given a full update on the 0.8.1 release so let me start with that:

1. The updates for the information is quite slow. Takes about 10 seconds after the song changes for the song information to change. Can this time be reduced?

2. For some songs the album art does not show up at all. This is strange as I follow an uniform policy for all my album art, i.e. in each folder which is an "album" I have a jpg file which is titled "cover.jpg". So, there should be no reason that the cover for one album shows up and the cover for another doesn't. Again, the album covers all show up in Amarok.

3. The method for controlling the volume is a little imprecise. Basically, it jumps between 33% to 50% to 64%. Smaller increments would be helpful. Also, it would be useful if the volume level was written on the side of the bar.

4. Now my test was very unscientific but over a period of 3 hours playing songs and using Tesla my battery drained about twice as fast as without using Tesla. I understand that Tesla needs to refresh and ping my machine very often, but is there any way to bring down the battery drain?

5. Finally, and this is purely cosmetic, the buttons for next track and previous track are a little small and a little too close to the play/pause. I'd say my fingers are average sized, but sometimes I end up hitting the wrong button.

I'd be happy to test out any new releases. If you put the download link either in an e-mail or in this thread then I can download straight onto my phone.

Thansk!

---

### Post by SeanHodges on 2009-10-04
> **abhiroopb said:**
> Hi Sean,

I definitely didn't get that e-mail. I do remember signing up for it and even having RSS feeds for all your pages on the Tesla website, however, like I said I didn't get any updates. We can either continue conversing on this thread, or you could let me know where I should sign up and I could subscribe to RSS feeds for those pages as well to keep me in the loop.

Thanks for the info, I'll take a look at the mailing list later, there must be something I haven't set right on Sourceforge.

> I haven't really given a full update on the 0.8.1 release so let me start with that:

Those points are definitely useful, I'll add them to the bug tracker and run through them soon as I get chance. The only thing I can see as particularly tricky is the battery consumption, as improving it will mean switching from SSH server to an optimised server that the user would have to install on their PC - It's still worth considering though.

> I'd be happy to test out any new releases. If you put the download link either in an e-mail or in this thread then I can download straight onto my phone.

Great, I'm not at home this weekend but I'll upload something when I get back.

Cheers

---

### Post by abhiroopb on 2009-10-04
Hi Sean,

Yes I can see why the battery consumption issue would be tricky. And, actually, one of the reasons I prefer your app is because there is no buggy java program that needs to be run on the host computer (such as gmote uses). Tesla is cleaner in that sense. However, it is up to you I guess how you decide to solve it! Perhaps if you made some sort of deb package that ran as a service in the background. But, please NO java app!! :P

Let me know if you need anything else.

---

### Post by SeanHodges on 2009-10-06
Sorry for the late reply, the real job has been consuming my time recently :)

> **abhiroopb said:**
> one of the reasons I prefer your app is because there is no buggy java program that needs to be run on the host computer (such as gmote uses). Tesla is cleaner in that sense.

I agree, and part of my motivation for continuing with Tesla after Gmote was announced was in the differences of server-side implementation. I intend to consider this area carefully before making any drastic changes from what we have now.

I've uploaded a test build here: [Tesla-0.8.2-abhiroopb1.apk]("http://seanhodges.co.uk/~sean/tesla-res/Tesla-0.8.2-abhiroopb1.apk"). It's a crude cut of the code, but it does demonstrate the playlist feature, and the new seek buttons (another feature you suggested a while ago). If you could let me know what you think, and give any feedback by this weekend, I'll try to make any necessary changes before I do the next release.

---

### Post by abhiroopb on 2009-10-06
Installed. Will update soon.

---

### Post by abhiroopb on 2009-10-06
Release Feedback:
1. Connecting seemed to take longer than usual (although this was a very unscientific test).

2. Play/Pause is quite slow. I.e. when I select play on my remote it pauses the song after xx

2. Seek Bar:
AMAROK: The buttons placed next to the seek bar move to the NEXT and PREVIOUS songs in Amarok, this makes them essentially the same as the buttons next to the play/pause buttons. 
VLC: In VLC the video jumps forward a couple of seconds (which is the desired effect).

3. Playlist:
AMAROK: The playlist shows up but selecting a song does not automatically change to that song.
VLC: Playlist works flawlessly, all the video files are displayed and selecting any one changes to that one.

4. Not sure if I mentioned this before but the shutdown button does not work (does nothing).

Features:
1. In Android when you type there is haptic feedback (i.e. when you press a key there is a slight vibration). This would be a useful feature to have. Not sure if the Android code allows this.

2. I would suggest adding a "search" feature to the playlist. Especially, for Amarok where I frequently have playlists with over 2000 songs (makes scrolling difficult!). Also perhaps incorporating artist/album fields.

3. Perhaps add a method of enqueing tracks.

4. Add a method of stopping after a certain track or after a certain period of time (i.e. a "sleep mode"). Also have the option of switching of the computer after the pre-selected track/time.

These features would probably add more bloat to a programme that seems to want to stay sleek and minimalistic. Therefore, these are only suggestions (ideas!) that you may want to think about.

---

### Post by abhiroopb on 2009-10-06
UPDATE:

Might just be this unpolished release but the battery drain has become a MAJOR problem. When I picked up my phone and downloaded the app the batter was at 35%. 

That was about 17 mins ago, and now the battery is at 15%. Even when I am browsing the web, or playing games it takes at least 1-2 hours before I see such a drastic drop.

UPDATE 2:

In the last 10 minutes battery dropped another 10%!

---

### Post by SeanHodges on 2009-10-06
I've added a lot of your feedback to the bug tracker, you can track them here: [http://sourceforge.net/apps/trac/android-tesla/report/1](http://sourceforge.net/apps/trac/android-tesla/report/1)

Though, of course I'll continue to give you updates as there is news.

> **abhiroopb said:**
> Might just be this unpolished release but the battery drain has become a MAJOR problem. When I picked up my phone and downloaded the app the batter was at 35%. 

That was about 17 mins ago, and now the battery is at 15%. Even when I am browsing the web, or playing games it takes at least 1-2 hours before I see such a drastic drop.

What is interesting is that I have not made any modifications in that build that should affect the battery drain. It should be the same as the previous 0.8.2 release.

I'll be interested to hear whether your increased battery drain problems continue after you've recharged a couple of times. I will do some tests at my end as well.

---

### Post by abhiroopb on 2009-10-06
Fair enough will do more testing then!

---

### Post by abhiroopb on 2009-10-08
Its hard for me to say definitively whether the new 0.8.2 is decreasing the battery quicker than previous builds. However, while the app is running the battery is definitely being drained faster.

I guess this makes sense as while Tesla is running it is almost as though I am using the phone (albeit without the screen being switched on). The app must get song information from the computer over wifi which I'm sure consumes the battery. If this is the case then I guess there isn't much you can do about it! Let me know how your tests go. Perhaps there is something on my phone or laptop that I can optimise.

---

### Post by SeanHodges on 2009-10-13
Hi abhiroobp,

Thanks for all your testing, I've finally got a release of 0.9 out. It includes a few fixes on top of your last custom build.

> **abhiroopb said:**
> Its hard for me to say definitively whether the new 0.8.2 is decreasing the battery quicker than previous builds. However, while the app is running the battery is definitely being drained faster.

This is definitely a side-effect of using the app, a little like using the Google maps app all the time, it requires a lot of power to maintain the Wifi connection.

> **abhiroopb said:**
> I guess this makes sense as while Tesla is running it is almost as though I am using the phone (albeit without the screen being switched on). The app must get song information from the computer over wifi which I'm sure consumes the battery. If this is the case then I guess there isn't much you can do about it! Let me know how your tests go. Perhaps there is something on my phone or laptop that I can optimise.

Unfortunately, there isn't a lot you can do about it right now. Because Tesla is using SSH, the app must maintain a Wifi connection as long as it is running. This means it has to keep the Wifi adapter awake and screen turned on. If the Wifi connection is lost, then the user will have to wait for it to reconnect before being able to control the PC again.

The amount of data being sent doesn't make a lot of difference, because the connection is always running. The only way to significantly reduce the power consumption will be to provide an alternative server-side service, that is better optimised for Tesla than SSH is.

At the moment, I'm going to leave things as they are, at least until the 1.0 release. After that, I hope to work on an optimised service that can be optionally used instead of SSH. I don't plan for it to be a Java app, so don't worry :)

Anyway, that's pretty much it for now. Still lots to do! By the way, I do like your idea for triggering a shutdown on alarm/end-of-playlist. It's in the bug tracker and I hope to take a look at adding it soon.

Also, can you give me a little more info on your shutdown button not working? Has it ever worked? Does Tesla crash when you try? Are you using KDE3, KDE4, Gnome, or something else? I've had no luck reproducing it so far.


Cheers,

Sean

---

### Post by abhiroopb on 2009-10-13
Thanks for the response. I know that a lot of my suggestions may add bloat so I may end up eating my words later, but, I guess it is a good idea to have a long feature-list so that you can add stuff in slowly.

Shut-down issue:

Running Gnome (Ubuntu Jaunty).
When I click on the RED shutdown button (top right corner) in Tesla a text box pops up saying: 
```
Confirm shut down
Are you sure you want to turn off the computer? 
```

I then click: Turn Off

Then I get a small message on the bottom of the screen that says:
[code] Your PC will shutdown[/code}

Then nothing happens on my computer (and Tesla exits to the opening screen).

So, I've tried it about 30 times till today, and JUST now I tried it and it worked! And I tried it again and it didn't work...strange behaviour!

By the way, do you know if it is possible to wake the PC either from sleep, hibernate or powered off using JUST the android phone? Is there any type of signal I can send over the wifi that turns it on? If there is it may be a cool addition to Tesla.

---

### Post by SeanHodges on 2009-10-14
> **abhiroopb said:**
> Thanks for the response. I know that a lot of my suggestions may add bloat so I may end up eating my words later, but, I guess it is a good idea to have a long feature-list so that you can add stuff in slowly.

Definitely. Whilst I obviously have my own expectations for this project, it's much better to shape it into something everyone will find useful. Many of your ideas have been very cool and I hope to find time to implement them as time allows. Recording them in the bug tracker will ensure that other developers can take a stab at doing them as well, which will hopefully speed up progress eventually.

> Shut-down issue:

Running Gnome (Ubuntu Jaunty).
When I click on the RED shutdown button (top right corner) in Tesla a text box pops up saying: 
```
Confirm shut down
Are you sure you want to turn off the computer? 
```

I then click: Turn Off

Then I get a small message on the bottom of the screen that says:
[code] Your PC will shutdown[/code}

Then nothing happens on my computer (and Tesla exits to the opening screen).

So, I've tried it about 30 times till today, and JUST now I tried it and it worked! And I tried it again and it didn't work...strange behaviour!

I agree it is strange behaviour. I'll have a play this week and see if I can reproduce what you are seeing. I must admit I've probably tested the shutdown button in KDE4 far more often than I have in Gnome, this intermittent issue is probably something I've missed so far. I'll let you know how I get on.

> By the way, do you know if it is possible to wake the PC either from sleep, hibernate or powered off using JUST the android phone? Is there any type of signal I can send over the wifi that turns it on? If there is it may be a cool addition to Tesla.

There is a way to turn on your PC by the network card ("Wake-on-LAN"), there are some instructions here: http://www.mythtv.org/wiki/Wake-on-LAN. It is possible that Tesla could send the "magic packet" to switch on your PC remotely.

The main issue is configuration. Tesla prefers convention over configuration, to try and make it easy for casual/novice users. This feature would probably have to be a special case, because you need to enable features in your BIOS and drop to the command-line to change low-level network settings on your PC. This doesn't prevent the feature from being a possibility though.

The second (smaller) issue is the login screen. The user would have to disable the login screen so that the PC was properly logged in by the time Tesla attempts to launch a media player. This won't be a problem on PC media servers, but it could be undesirable for someone using Tesla with their secured desktop PC.

I'll add it to the list though. I think it will be a great feature for those who are happy to put up with the caveats.

---

### Post by abhiroopb on 2009-10-14
Ah yes Wake on LAN I have heard of that. In fact now that I recall I think I tried it and found that it was too complicated and my BIOS did not support it  (or at least I couldn't find an option for it).

I had this "ideal" setting I thought of a while back...

I set-up Locale in such a way so that when I walk through my front door my computer switches on (using the Wake-on-LAN feature that you mentioned). I already have Locale set-up so that my WiFi turns on when I'm near my house. Next, I have Tesla switch on. So, by the time I reach my computer I have my music playing! Our generation has become lazy!! Anyway I want to sort out Wake-on-LAN so I don't have to keep my computer on all the time.

Thanks for the update! I've installed the 0.9 versions and nothing new (problems wise).

Cheers

---

### Post by abhiroopb on 2009-10-14
By the way, responsiveness in VLC is much faster than Amarok.

---

### Post by abhiroopb on 2009-10-19
Sorry I haven't updated in a while...

1. In the latest release clicking the seek button on Amarok works without a problem (i.e. it jumps forward and backwards by a few seconds).

2. The playlist works fine in Amarok as well (i.e. clicking on a song in a playlist switches to that song). 

3. Loading a playlist is VERY slow. I have a 2000 song playlist and its probably slow because of the size of the playlist, could this be optimised so it loads faster?

Feature Request:
1. Near the top left corner there is an icon of the currently running media player. To change a media player you need to do the following: click on menu, click on change media player, scroll the list and click on the media player to change to it. As you can see this is quite a few steps. Would it be possible to put icons for two (or three media players) in the top left corner). I personally only use VLC and amarok so for me the entire list a little useless. I'm sure that for virtually everyone using Tesla they would only use a few of the apps (and no-one would actually need to ever see the entire list). What I would suggest is an option somewhere to select which apps would show up on the main screen. So, in the preferences you can put a simple check-box list where the user can select which players they would like displayed. 

2. Add the length of the track (i.e. the number of hrs, mins and secs of the song/video).

3. This is just a stupid problem I'm having...Basically, I'll be watching a video and then after it finishes I'll have to move to my computer to lock the screen (as I usually lock the screen over night). Would it be possible to put a lock screen option in the app? (Wow this app is making me very very lazy!)

Cheers!

---

### Post by SeanHodges on 2009-10-21
Hey abhiroopb,

> **abhiroopb said:**
> 1. In the latest release clicking the seek button on Amarok works without a problem (i.e. it jumps forward and backwards by a few seconds).

2. The playlist works fine in Amarok as well (i.e. clicking on a song in a playlist switches to that song). 

Great stuff, we're getting there slowly :)

> 3. Loading a playlist is VERY slow. I have a 2000 song playlist and its probably slow because of the size of the playlist, could this be optimised so it loads faster?

I will take a look at optimising the algorithms soon, right now I'm concentrating on finishing Rhythmbox support. After that, I'll look at handling larger lists better. Obviously the improvements will be limited to the performance of Amarok's own API.

> Feature Request:
1. Near the top left corner there is an icon of the currently running media player. To change a media player you need to do the following: click on menu, click on change media player, scroll the list and click on the media player to change to it. As you can see this is quite a few steps. Would it be possible to put icons for two (or three media players) in the top left corner). I personally only use VLC and amarok so for me the entire list a little useless. I'm sure that for virtually everyone using Tesla they would only use a few of the apps (and no-one would actually need to ever see the entire list). What I would suggest is an option somewhere to select which apps would show up on the main screen. So, in the preferences you can put a simple check-box list where the user can select which players they would like displayed. 

I like this idea. I actually had other plans for the top left corner (namely, an eject button for playing a different song/video from the filesystem), the icon was just added to fill the empty space in the meantime. I do think that some space should be made to add this feature as well though. 

I think the most difficult part will be making a simple configuration dialog to map the "quick toggle" buttons to their media players... Perhaps Tesla should keep a score of the players used, and display the most frequently used?

> 2. Add the length of the track (i.e. the number of hrs, mins and secs of the song/video).

This will be tricky to duplicate across all the supported players (some only provide the progress as a percentage for example). I'll add it to the bug list and see if there is some compromise to be made.


> 3. This is just a stupid problem I'm having...Basically, I'll be watching a video and then after it finishes I'll have to move to my computer to lock the screen (as I usually lock the screen over night). Would it be possible to put a lock screen option in the app? (Wow this app is making me very very lazy!)

This leads into some thoughts I've been having about the shutdown mechanism, I think I'm going to map out a slightly more comprehensive shutdown control, with a delay option ("end of playlist", etc) and the ability to lock the screen / suspend instead of shut down. I'll brainstorm some ideas over the weekend, but if you have any suggestions in this area feel free to share them.

Oh and BTW, I think I've reproduced your shutdown button issue, can you confirm that the shutdown button only stops working after you have opened Amarok for the first time? I believe Amarok is starting some KDE session components, and making Tesla think it is running under KDE rather than Gnome... I've written a fix that I hope to include in the next release, assuming this is the cause of the problem.

My plans right now are to wind up some of the remaining features I've been working on, and get a stable 1.0 release out. Once that is done, I hope to move onto some more adventurous features. I think we're nearly at the stage that someone can play around with Tesla and not get bombarded with crashes and error messages, which sounds like a good time to wrap up a stable release :)

---

### Post by abhiroopb on 2009-10-22
> 
I will take a look at optimising the algorithms soon, right now I'm concentrating on finishing Rhythmbox support. After that, I'll look at handling larger lists better. Obviously the improvements will be limited to the performance of Amarok's own API.
Recently, its been crashing when trying to load my massive playlist. Perhaps instead of showing the entire playlist load a blank list where you can search. Usually, searching for an artist, album or song usually decreases the size of the playlist considerably. I would rarely want to scan the entire playlist anyway, so, by including a search option it would automatically decrease the size of the playlist.

> 
I like this idea. I actually had other plans for the top left corner (namely, an eject button for playing a different song/video from the filesystem), the icon was just added to fill the empty space in the meantime. I do think that some space should be made to add this feature as well though. 

I think the most difficult part will be making a simple configuration dialog to map the "quick toggle" buttons to their media players... Perhaps Tesla should keep a score of the players used, and display the most frequently used?

The "eject" button actually sounds like a good idea. But, (and I'm sure this applies to most people) when you choose a song you don't start it up from the filesystem, you would usually search in your media player. The only occasion where you would search your filesystem is if you have a video. Since there aren't any good video managers most people would still click on the video in their filesystem and have VLC launch. This would be very convenient as it would remove the need to be near the computer when starting up a new video. Still you could add this elsewhere (even as a separate menu option).

Your idea of Tesla keeping score of the most frequently used app is a good idea as it will remove the need for another configuration option. I guess its up to you which is easier to implement and use (without getting buggy!).

> 
This will be tricky to duplicate across all the supported players (some only provide the progress as a percentage for example). I'll add it to the bug list and see if there is some compromise to be made.

If its too difficult don't worry about it. Its not essential. However, I think it would be MOST useful for videos on VLC. A song is usually too short for the length to be all that relevant. On the other hand a video is usually quite long and it is useful to know how long it is and how long it will take to finish.

> 
This leads into some thoughts I've been having about the shutdown mechanism, I think I'm going to map out a slightly more comprehensive shutdown control, with a delay option ("end of playlist", etc) and the ability to lock the screen / suspend instead of shut down. I'll brainstorm some ideas over the weekend, but if you have any suggestions in this area feel free to share them.
For me personally I don't really have a pressing need to shut-down my computer. I'm quite happy to leave my computer running. And (again generalising a LOT) I don't think that a lot of people would actually want their computer to shut-down. Sleep/hibernate/lock screen are better options. The other problem with the current shutdown option is that it opens up the shutdown dialog. This is really annoying as you need to wait 60s. for the shutdown to occur. I think upon pressing the button it should: a) sleep, or b) lock the screen (without any delay). But, the end of playlist feature would also be very useful. This should perhaps just be an option to pause the player rather than a full shutdown. In any case locking the screen would not stop the player.

> 
Oh and BTW, I think I've reproduced your shutdown button issue, can you confirm that the shutdown button only stops working after you have opened Amarok for the first time? I believe Amarok is starting some KDE session components, and making Tesla think it is running under KDE rather than Gnome... I've written a fix that I hope to include in the next release, assuming this is the cause of the problem.
When I turn on my PC amarok starts up automatically (I have put it in the startup programs list). And any time I try to shut down using the Tesla app it doesn't do anything. After restarting amarok I thought I would test it out, but Tesla got stuck on "Connecting with computer". Obviously I hadn't changed anything on the computer except for the fact that I had restarted amarok. Tried restarting amarok and trying to connect Tesla and no luck. I can't connect to VLC either. I'm not sure what happened. I will try restarting my computer and trying again later. (NB: both VLC and amarok were already running on the computer when I tried launching Tesla).


> 
My plans right now are to wind up some of the remaining features I've been working on, and get a stable 1.0 release out. Once that is done, I hope to move onto some more adventurous features. I think we're nearly at the stage that someone can play around with Tesla and not get bombarded with crashes and error messages, which sounds like a good time to wrap up a stable release 
Good luck let me know if I can help any further!

---

### Post by SeanHodges on 2009-10-29
> **abhiroopb said:**
> Recently, its been crashing when trying to load my massive playlist. Perhaps instead of showing the entire playlist load a blank list where you can search. Usually, searching for an artist, album or song usually decreases the size of the playlist considerably. I would rarely want to scan the entire playlist anyway, so, by including a search option it would automatically decrease the size of the playlist.

I think some kind of search feature will be very useful, but as not everyone has large playlists, it is also beneficial to display the playlist initially (or at least the first 20-30 results)...

The big bottleneck is transferring the data in the first place from the player to Tesla. I might look into some way of storing the retrieved playlist on the PC, and retrieving "pages" one at a time.

This may actually take us further from our goal of having a search feature on the playlist, as Tesla will have to send a send query to the PC to get the the results, instead of just searching the items in it's own UI. But the advantage will be the ability to navigate around the playlist without necessarily knowing what's in it (e.g. when using dynamic playlists in Amarok).

> The "eject" button actually sounds like a good idea. But, (and I'm sure this applies to most people) when you choose a song you don't start it up from the filesystem, you would usually search in your media player. The only occasion where you would search your filesystem is if you have a video.

I agree. The problem is that I haven't seen a media player yet that exposes it's own "collection manager" through an API. That functionality is pretty much closed off, so Tesla will have to do it itself. I do have some ideas that will avoid having to navigate around the filesystem, once I've put some of my ideas together I'll let you know.

> When I turn on my PC amarok starts up automatically (I have put it in the startup programs list). And any time I try to shut down using the Tesla app it doesn't do anything. After restarting amarok I thought I would test it out, but Tesla got stuck on "Connecting with computer". Obviously I hadn't changed anything on the computer except for the fact that I had restarted amarok. Tried restarting amarok and trying to connect Tesla and no luck. I can't connect to VLC either. I'm not sure what happened. I will try restarting my computer and trying again later. (NB: both VLC and amarok were already running on the computer when I tried launching Tesla).

Do let me know if you discover anything more about this behaviour. I've made a fix in the new 0.10 release that might fix the shutdown button issue, but that connecting issue is worrying...

---

### Post by abhiroopb on 2009-10-29
> **SeanHodges said:**
> I think some kind of search feature will be very useful, but as not everyone has large playlists, it is also beneficial to display the playlist initially (or at least the first 20-30 results)...

The big bottleneck is transferring the data in the first place from the player to Tesla. I might look into some way of storing the retrieved playlist on the PC, and retrieving "pages" one at a time.

This may actually take us further from our goal of having a search feature on the playlist, as Tesla will have to send a send query to the PC to get the the results, instead of just searching the items in it's own UI. But the advantage will be the ability to navigate around the playlist without necessarily knowing what's in it (e.g. when using dynamic playlists in Amarok).


I agree not everyone has large playlists so it's definitely a good idea to show the playlists first. Perhaps have the playlist button  only pull up the first 50-100 tracks. The thing about playlists (at least for me) is that I make them with songs I like so I usually don't have to look to far when changing a song. So, if I have about 50 options that would be sufficient for me. 50 random options (from a playlist of say 2000) would be fine for me. On the other hand (and this leads on to your collections manager point) there are times I like to find a particular song and listen to it. IN these cases if it's in the playlist its not a big problem as I can easily browse for it or search for it (once these are added), however, if it is not in the playlist then I would have to search my collection, which as you say can't really be done.

> **SeanHodges said:**
> 
I agree. The problem is that I haven't seen a media player yet that exposes it's own "collection manager" through an API. That functionality is pretty much closed off, so Tesla will have to do it itself. I do have some ideas that will avoid having to navigate around the filesystem, once I've put some of my ideas together I'll let you know.
 

I didn't realise this was the case. If it is not possible to search the collections of a media player then such a feature would be useful. However, I'd imagine people would have a hard time finding a specific track in the file system. VLC remote actually employs a function similar to this. Again it is more useful (in my opinion) with videos. 


> **SeanHodges said:**
> 
Do let me know if you discover anything more about this behaviour. I've made a fix in the new 0.10 release that might fix the shutdown button issue, but that connecting issue is worrying...

I think it was just a fluke! Working fine now. 

I've screwed up my sound in Ubuntu (added/deleted packages). Unfortunately, I have my Bar exams for the next two weeks so this will be my last update for a while!

Good luck and keep me posted.

---

### Post by SeanHodges on 2009-10-29
OK abhiroopb, well thanks for all your help so far, you've been very helpful. It's always good to have someone to bounce ideas off of.

Good luck with your bar exams!

---

### Post by abhiroopb on 2009-11-08
Hi SeanHodges

Exams over and I'm back.

Just upgraded to Karmic. Noticed a problem connecting to VLC: "Error Code 833614".

I immediately realised that this may-be because d-bus was no longer set (as I had re-installed everything). I made the changes and it works fine.

My suggestion is to make this particular error a little more descriptive with a guide on how to change the VLC Settings. The error is relatively easy to solve so people should not have to go digging to look for it. 

Anyway are there any cool new updates?

best!

---

### Post by SeanHodges on 2009-11-09
Hi abhiroobp,

I hope the exams go well for you.

Things have been fairly quiet for Tesla recently, though I have found time to implement a few new features that I hope to release within the next couple of days. One feature that you will find particularly interesting is the ability to suspend/lock-screen instead of shutdown when the power button is pressed. I've also spent a bit of time working on battery consumption improvements.

I still haven't had the chance to upgrade to Karmic, but I'm hoping to very soon. The VLC issue you describe makes sense, I'll look into some way of detecting if the DBUS session is available, and display the VLC setup instructions instead of an error when it is not.

I'll let you know as soon as I get the release pushed out.


Cheers,

Sean

---

### Post by SeanHodges on 2009-11-11
> **SeanHodges said:**
> I'll let you know as soon as I get the release pushed out.

The release is out :)

I'm still edging slowly towards a 1.0 release. If you could take a look at this one and let me know of any issues you have, that would be great. 

Also, of the pending features/bugs you have mentioned so far, which ones do you feel would be most important to you? I'm getting a fair few requests these days, and I would like to prioritise them a little better so people aren't waiting for "show stoppers" whilst I work on "nice haves".

---

### Post by abhiroopb on 2009-11-11
Just installed version 0.11. Changes look good. Will test it out throughout today.

Is there a way to list out all the features? I can't remember what all of them were.

Of the top of my head something that annoyed me last night:

I was trying to change system volume and noticed three problems:

1. The increments are too high (e.g. 66% to 82%)

2. The volume amount shown was wrong. 

3. Changing the volume is a bit difficult (as the increments are too high I guess)

But, I'll have a closer look at the updated version.

Just tried the lock screen and nothing happened.

---

### Post by abhiroopb on 2009-11-11
Hasn't been connecting suddenly. Was working when I first tried it, but, not working any longer.

Any thoughts?

---

### Post by SeanHodges on 2009-11-12
> **abhiroopb said:**
> Just installed version 0.11. Changes look good. Will test it out throughout today.

Is there a way to list out all the features? I can't remember what all of them were.

You can see the pending feature/bug list here:

[http://sourceforge.net/apps/trac/android-tesla/report/1](http://sourceforge.net/apps/trac/android-tesla/report/1)

> Of the top of my head something that annoyed me last night:

I was trying to change system volume and noticed three problems:

1. The increments are too high (e.g. 66% to 82%)

2. The volume amount shown was wrong. 

3. Changing the volume is a bit difficult (as the increments are too high I guess)

But, I'll have a closer look at the updated version.

Work on the system volume handling is still pending. Feel free to mark it as one of your high priorities, and I'll see if I can take a look at it soon.

> Just tried the lock screen and nothing happened.

Could you run the following command in a terminal on your PC, and let me know if it locks your screen correctly (and if not, post up any errors it gives)?

```
DISPLAY=:0 dbus-send --session --print-reply --dest=org.kde.krunner --type="method_call" /ScreenSaver org.freedesktop.ScreenSaver.Lock &> /dev/null ;dbus-send --session --print-reply --dest=org.gnome.ScreenSaver --type="method_call" / org.gnome.ScreenSaver.Lock &> /dev/null
```

The lock screen mode works on both of my machines (KDE and Gnome), though my real job is keeping me from upgrading to Karmic right now - which may be the issue here.

> Hasn't been connecting suddenly. Was working when I first tried it, but, not working any longer.

Any thoughts?

Is it failing to connect with an error message, or just hanging indefinitely at the "Connecting to computer" progress dialog?

I'm doing some diagnostics on the connection process at the moment. I'm starting to think there is a little more to the intermittent connection bugs than Wifi network issues alone.

One thing I can confirm is that very occasionally (particularly when Tesla crashes) the back-end service will not terminate correctly. This causes the next connection attempt to hang, because Android thinks that Tesla is still running elsewhere. I've seen it happen a couple of times now, and worked around it by killing the old background "Tesla" instance using TaskKiller (any task manager should do though).

Let me know if this helps the next time you have a problem connecting...

---

### Post by abhiroopb on 2009-11-13
> **SeanHodges said:**
> You can see the pending feature/bug list here:

[http://sourceforge.net/apps/trac/android-tesla/report/1](http://sourceforge.net/apps/trac/android-tesla/report/1)



Work on the system volume handling is still pending. Feel free to mark it as one of your high priorities, and I'll see if I can take a look at it soon.



I'll have a look at this over the weekend and let you know. But off the top of my head two important things:

1. The connection needs to be made faster (more on this below).
2. The volume controls needs to be made more refined.


> **SeanHodges said:**
> 
Could you run the following command in a terminal on your PC, and let me know if it locks your screen correctly (and if not, post up any errors it gives)?

```
DISPLAY=:0 dbus-send --session --print-reply --dest=org.kde.krunner --type="method_call" /ScreenSaver org.freedesktop.ScreenSaver.Lock &> /dev/null ;dbus-send --session --print-reply --dest=org.gnome.ScreenSaver --type="method_call" / org.gnome.ScreenSaver.Lock &> /dev/null
```

The lock screen mode works on both of my machines (KDE and Gnome), though my real job is keeping me from upgrading to Karmic right now - which may be the issue here.


The command locked the screen without any errors. But, it still doesn't lock when I try it through Tesla.

> **SeanHodges said:**
> 
Is it failing to connect with an error message, or just hanging indefinitely at the "Connecting to computer" progress dialog?

I'm doing some diagnostics on the connection process at the moment. I'm starting to think there is a little more to the intermittent connection bugs than Wifi network issues alone.

One thing I can confirm is that very occasionally (particularly when Tesla crashes) the back-end service will not terminate correctly. This causes the next connection attempt to hang, because Android thinks that Tesla is still running elsewhere. I've seen it happen a couple of times now, and worked around it by killing the old background "Tesla" instance using TaskKiller (any task manager should do though).

Let me know if this helps the next time you have a problem connecting...

It did hang at the connecting screen without any errors. Although it worked after I killed the process. 

Also couple of problems (application specific):

VLC: I get the following error right after it appears to finish connecting: "The media player is no longer available" (connecting is also slow). Restarting VLC had no effect. I restarted my computer and it got  stuck at "Connecting with computer". I closed the app, killed the background process and restarted and it connected after a while. But, the graphics were messed up, basically, the album cover and tag information are pushed to the top of the screen (covering the player icon and shutdown button). This resets after a while.

Amarok: Connecting with computer sign takes a long time (i.e. slow). Graphics are skewed (as above). 

So, right now I think the main thing is optimization and tweaking these small issues. Basically, before adding new features I think its important that these hiccups are sorted out. For example, I am sub-consciously put-off using the app because it takes a while to connect. Ideally whenever I play a video or a song I should be reaching for Tesla, but this doesn't really seem to happen and I think the main reason is because it has become a little unpredictable. 

But, I'm sure these are minor things and can be tweaked.

I'll post again with the features I find are most important.

Thanks!

---

### Post by SeanHodges on 2009-11-19
Hey abhiroopb,

After spending some time testing in my old Android 1.5 emulator, I've seen the graphics quirk that you reported. I have a fix for it that I'll release it as soon as possible. Looks like the 1.5 -> 1.6 migration isn't as simple as the documentation suggests. (the 1.6 migration was needed to fix layout issues on the HTC Tattoo phone)

I've also made some progress on the "player is not available" issue as well, I was checking if VLC was running before it had sometimes launched fully. That message is a fix for different bug; to do with a Tesla error message that used to get thrown when the player is closed on the PC.


Connection issues are my next task. I have had a few reports of slow connecting from various people. Unfortunately, there appears to be no obvious pattern to these issues, so far I've been making stab-in-the-dark tweaks to the SSH protocol settings, with varying success. There are still some tricks up my sleeve to improve this further.

Having said that, the cold hard truth is that SSH isn't going to give us connection speeds better than ~10secs (over local Wifi), to get better than that I'll need to start working on a new PC service. I do intend to look into that, but I want the 1.0 release out first (e.g. a stable user experience with just SSH).


I agree with you that fixing the existing issues is a priority over new functionality. In fact, I have a number of new features that have been delayed until the stable 1.0 release is finished. Hopefully this will eventually become a reality, as bug fixing can become a very tiresome process when you're the only developer on a project :)

---

### Post by abhiroopb on 2009-11-19
Any thoughts on the lock screen issue?

as for features (ranked in order of priority):

1. Song info slow to update (also play/pause and track change, but I fear this is a problem with SSH).
2. Enhance playlist screen (also fix for large playlists)
3. Volume control issues (including more accurate changes, actual volume and ability to change using the android volume buttons on the side).
4. Playing media length
5. Album art (on-line retrieval and correct display)
6. Stop/shutdown on alarm (or at least stop track after certain duration).
7. Haptic feedback. 
8. Power on remotely (don't think my laptop supports this anyway!)

Hope all this helps!

---

### Post by SeanHodges on 2009-11-19
I forgot to mention the lock screen issue. I recently installed Karmic on one of my machines, so I can test it this weekend. Hopefully testing on a Karmic set-up will shed some light on the subject.

> 1. Song info slow to update (also play/pause and track change, but I fear this is a problem with SSH).

On most players (including Amarok 2) the song info and playback controls are very responsive; with the exception when downloading new a CD cover (when only the song info retrieval should be slow).

I've noticed when testing on my system that the D-Cop commands to Amarok take a few seconds to complete, when running the commands in a terminal in Gnome like this:

```
dcop amarok player next
```

Let me know if you notice the same issue, because if you do, we might need to change the way we interact with Amarok 1 in Tesla (or find a work-around for this issue).

---

### Post by abhiroopb on 2009-11-19
Running the command in a terminal is instantaneous there is no delay at all :S

---

### Post by leshachek on 2009-11-22
Excellent, working fine for me on Android Hero.
I tested Amarok and VLC running on Kubuntu 9.10.
Apparently would be nice to have more control on hosting applications.
For instance, having few hosts in the list to control.

---

### Post by leshachek on 2009-11-22
> **abhiroopb said:**
> 
....
VLC: I get the following error right after it appears to finish connecting: "The media player is no longer available" (connecting is also slow). Restarting VLC had no effect. I restarted my computer and it got  stuck at "Connecting with computer". I closed the app, killed the background process and restarted and it connected after a while. But, the graphics were messed up, basically, the album cover and tag information are pushed to the top of the screen (covering the player icon and shutdown button). This resets after a while.

....
Thanks!

I had that error till I stop VLC running and was able to connect and start VLC with no problem on Hero.
Before that Tesla was blocked by a firewall running on my hosting computer. I had to allow connections from my Android mobile.

---

### Post by SeanHodges on 2009-11-24
> **leshachek said:**
> Excellent, working fine for me on Android Hero.
I tested Amarok and VLC running on Kubuntu 9.10.
Apparently would be nice to have more control on hosting applications.
For instance, having few hosts in the list to control.

Thanks leshachek, I'll make a note of your suggestion on the bug tracker. If I understand correctly, you're asking for some kind of server list similar to this?

[IMG]http://android-vlc-remote.googlecode.com/svn/trunk/screenshots/settings.png[/IMG]

Great to hear it's working for you.

---

### Post by SeanHodges on 2009-11-24
Hey abhiroopb,

Sorry for the long delay, I've been keeping my head down trying to get some of these connection issues tidied up. Hopefully the new release 0.11.1 will clear up a lot of these.

I've only really concentrated on the connection issues (performance and stability), so the volume control is still basic, and the large playlist bug is not fixed yet. You should, however, find the connection speed significantly faster - pretty much as fast as it will realistically go right now.

The new release also has a fix for the graphics glitch in Android 1.5. Seems the old UI rendering needed to draw the screen elements in a particular order. Please let me know if you don't see any difference, I only have the Android emulator to test with for 1.5 so there are no guarantees.

> **abhiroopb said:**
> Running the command in a terminal is instantaneous there is no delay at all :S

I think I was jumping to conclusions. Running my own test again seems to have no delay, just as you said. There must have been some wierd issue with my PC that day. We'll have to keep an eye on this responsiveness issue in Amarok 1.4 - You're pretty much the only person reporting bugs with Amarok 1.4, so your input is particularly valuable for this player.

---

### Post by abhiroopb on 2009-11-24
Just installed the 0.11.1 version.

1. Initial connection seems faster and the information regarding the connection is helpful as it tells you what is happening. So, the wait seems shorter.

2. Amarok/VLC: pause/play is almost instant. As it stands unless there is some bug that crops up connection and control of the player seems perfect. 

3. Lock screen is also working.

4. For some reason NONE of my album covers are showing up in Tesla anymore.

5. I also tested the playlist and with 151 tracks it takes about 2 secs to load. Did notice a really interesting bug: after the list is displayed if I click on song x it plays the song that is immediately after song x (every time). Seems like a simple coding error.

6. There is no longer any graphics glitch. But, I have noticed that the pause/play button does not change between the pause symbol and the play symbol.

As a side-note have you got any intention of putting the app in the android market? Would make it easier to update.

Thannks, glad to be of help.

---

### Post by SeanHodges on 2009-11-25
Sounds like we're doing much better with this release :)

> 4. For some reason NONE of my album covers are showing up in Tesla anymore.

I've noticed that behaviour recently too. My tests so far seem to only be album covers that Tesla has not already retrieved in the past.

> 5. I also tested the playlist and with 151 tracks it takes about 2 secs to load. Did notice a really interesting bug: after the list is displayed if I click on song x it plays the song that is immediately after song x (every time). Seems like a simple coding error.

I thought I'd seem the last of this :( The problem is Amarok 1.x playlists start from track "0", whilst Amarok 2.x playlists start from track "1" - It took a lot of effort to get it working correctly on both players, and it looks like that has broken again.

I'll take a look at the code again, see if there is something else going on.

> 6. There is no longer any graphics glitch. But, I have noticed that the pause/play button does not change between the pause symbol and the play symbol.

Hmm, it's working for me.. Keep me updated on this, it might only be happening under certain circumstances.

> As a side-note have you got any intention of putting the app in the android market? Would make it easier to update.

Definitely. I will be uploading Tesla to the Android Market as soon as it reaches 1.0 (which is basically when the major bugs are ironed out, and a couple of key features are completed). If I rush it into the Android Market, it will suffer a flurry of negative feedback and get buried at the bottom of the app list in no time. Having said that, I think we're pretty close to a stable version now - I just need to focus on the biggest issues right now.

In the meantime, you can get automatic updates using the AndAppStore client, which works pretty much the same as Google's Android Market client: [http://andappstore.com/AndroidApplications/apps/AndAppStore_Client](http://andappstore.com/AndroidApplications/apps/AndAppStore_Client)

---

### Post by abhiroopb on 2009-11-27
Again glad to be of help. 

Seems the playlist problem is bigger than I thought at first.

I think the play/pause feature was just a temporary glitch, seems to have disappeared.

Thats a good point, better to wait once the app is completely polished. Would definitely like to see Tesla with 5 star ratings.

A feature that would be useful would be a widget. May have mentioned this before but it's quite useful as a remote is only really needed to change tracks on occasion and having a dedicated app running becomes problematic. For example, if I exit the app to open an e-mail or sms I need to reconnect. The widget would ideally be 4x1 on the android home screen one side would have a play/pause button, and the back/forward button, the middle would display the name of the track and the other side could have menu information, etc.

Cheers

---

### Post by abhiroopb on 2009-12-04
Sean:

I am a dropbox user and I noticed that they are attempting to make an android app. Indeed it is a highly requested feature. I have also heard they may be looking for developers. I am sure you are very busy but I thought you may be interested.

Cheers
[https://www.dropbox.com/votebox/3/android-app](https://www.dropbox.com/votebox/3/android-app)

---

### Post by SeanHodges on 2009-12-09
Hey abhiroopb,

Sorry for the late reply, I haven't disappeared :)

> **abhiroopb said:**
> I am a dropbox user and I noticed that they are attempting to make an android app. Indeed it is a highly requested feature. I have also heard they may be looking for developers. I am sure you are very busy but I thought you may be interested.

The project sounds very interesting, although it appears I need to log into Dropbox to read the page you linked...

I'll take another look over the weekend, but if you get chance to copy and paste a summary from that link you gave me I'd be interested to take a look.

On the other subject: I have been making some progress with Tesla. I have a few overdue fixes, and a finally a collection browser :) I'm hoping to get another release very soon, but I'm trying to enforce some more rigorous testing before distributing new builds from now on. With a little luck I'll have it ready by this weekend, if not, I might just roll you a custom release to help me with the testing...

---

### Post by sleepy_head on 2009-12-11
hej,

i'm using Tesla-0.11.1. the ssh connection works fine, very fast :) but i get the error "**the media player is no longer available**". i tried to start amarok, kaffeine, VLC and dragon player.

i'm using:
[LIST]
[*]amarok 2.2.0
[*]kaffeine 1.0-pre2 (oke i didn't expect this version working fine)
[*]VLC 1.0.2
[*]dragon player 2.0
[/LIST]

are these versions not yet supported? 

ask if you need any more information and sry for my bad english ;)

---

### Post by SeanHodges on 2009-12-11
> **sleepy_head said:**
> i'm using Tesla-0.11.1. the ssh connection works fine, very fast :) but i get the error "**the media player is no longer available**". i tried to start amarok, kaffeine, VLC and dragon player.

i'm using:
[LIST]
[*]amarok 2.2.0
[*]kaffeine 1.0-pre2 (oke i didn't expect this version working fine)
[*]VLC 1.0.2
[*]dragon player 2.0
[/LIST]

are these versions not yet supported?

They should all be supported fine. I'm not sure why you're getting that message, it should appear when Tesla tests if the media player is running and gets back false. 

I haven't seen a situation so far that applies to every player (as you describe), can you check that an old version of Tesla is not still running in the background? You can check this with a task manager app like TasKiller.

---

### Post by sleepy_head on 2009-12-11
i installed tesla the first time. i also thought this must be an error if the player is not running, but they were :/

ah oke i edited the ssh port to 22 back and it works. BUT for amarok: i can't do anything. nothing happens if i say pause or seek forward.

---

### Post by SeanHodges on 2009-12-13
> **sleepy_head said:**
> ah oke i edited the ssh port to 22 back and it works.
 
You should be able to use Tesla when SSH is on a different port, by adding the port after a semicolon in your hostname e.g. 192.168.0.2:447

If this isn't working for you please let me know so it can be fixed.

> BUT for amarok: i can't do anything. nothing happens if i say pause or seek forward.

Hmm, I assume you have some music added to your playlist window? If no commands are being successfully sent to your PC, you should be getting an error message. Are you getting song information and album artwork appear in the middle of the screen?

If you could play around with the playback buttons / volume control and report any errors you see, I'll have a think about what might be causing this problem.

---

### Post by sleepy_head on 2009-12-14
hmmm i don't know what i've done. i changed port to 2233 and i get the playlist, cover, etc and everything works fine with amarok.

if i change the player to kaffeine i get the same error again "the media player is no longer available". i started the video on my pc, so there's running some stuff and i thought i wanna pause kaffeine (1.0-pre2). it works with dragonplayer so i assume my kaffeine version won't work ;)

so far so good :) seems everythings besides kaffeine works fine. thanks for all your answers!

---

### Post by SeanHodges on 2009-12-16
> **sleepy_head said:**
> so far so good :) seems everythings besides kaffeine works fine. thanks for all your answers!

Ah, I've just looked up Kaffeine 1.0-pre2 and discovered it has switched from DCOP to DBUS. I expected that to happen eventually, but it basically means Tesla will not work with the latest version until the back-end is updated.

I've added a bug report ([http://sourceforge.net/apps/trac/android-tesla/ticket/61](http://sourceforge.net/apps/trac/android-tesla/ticket/61)) but I think it would be wise to wait until the 1.0 proper is released before attempting to bind to all of the new API, otherwise the commands are likely to be a moving target. 

However, if you are a developer, and would like to take on the task sooner, let me know and I'll be happy to help you out getting a fix together. The code in Tesla is open-source, and it would be great to get some help on the project :)

If you are not a developer, please feel free to give me a nudge on this issue when 1.0 is released. I would like to ensure Kaffeine support is kept up-to-date.

---

### Post by SeanHodges on 2009-12-16
> **abhiroopb said:**
> Again glad to be of help. 

Seems the playlist problem is bigger than I thought at first.

I think the play/pause feature was just a temporary glitch, seems to have disappeared.

Thats a good point, better to wait once the app is completely polished. Would definitely like to see Tesla with 5 star ratings.

Hey abhiroopb,

Please be sure to update to the latest version of Tesla, there are a couple of fixes in there that will be of particular interest to you :)

I've fixed the playlist index bug in Amarok 1.4, so that should work now. I've also made the volume control more accurate, it now changes the volume consistently by 5%.

> A feature that would be useful would be a widget. May have mentioned this before but it's quite useful as a remote is only really needed to change tracks on occasion and having a dedicated app running becomes problematic. For example, if I exit the app to open an e-mail or sms I need to reconnect. The widget would ideally be 4x1 on the android home screen one side would have a play/pause button, and the back/forward button, the middle would display the name of the track and the other side could have menu information, etc.

Actually, you're not the only one to suggest a widget. I like the idea, but I'm a bit worried about the potential battery consumption that it would require. The advantage with the dedicated app is that it is quite clear to the user when the remote control is actively connected to their computer (because it is running), so disconnecting to save battery power is fairly easy.

I'll add a note in the bug tracker about this, because it would be a good feature to have (partly for the reasons you already gave). If we can work out some way that it can be practical (e.g. doesn't keep a connection going all the time, sapping up the battery life), then the rest of the work should be fairly trivial.

---

### Post by sleepy_head on 2009-12-16
> **SeanHodges said:**
> However, if you are a developer, and would like to take on the task sooner, let me know and I'll be happy to help you out getting a fix together. The code in Tesla is open-source, and it would be great to get some help on the project :)

If you are not a developer, please feel free to give me a nudge on this issue when 1.0 is released. I would like to ensure Kaffeine support is kept up-to-date.

Sadly i'm not a developer :| but i'll leave a message as soon as 1.0 is out :)

i just really like unsupported pre-releases :D

---

### Post by abhiroopb on 2009-12-19
> **SeanHodges said:**
> Hey abhiroopb,

Sorry for the late reply, I haven't disappeared :)

The project sounds very interesting, although it appears I need to log into Dropbox to read the page you linked...

I'll take another look over the weekend, but if you get chance to copy and paste a summary from that link you gave me I'd be interested to take a look.



Sean,

Sorry for the delay I have been on vacation.

Actually, I didn't see a particular job posting or anything like that. Just that dropbox have a voting section where you can vote for things you want the dropbox team to do and an android app is one of the top five (that was what the page was about). 

Anyway I installed the latest Tesla:

1. Collection browser gave me the following error:
```

Failed to send query to remote machine
...

```
There is a bunch of other code below it but it is quite a lot to reproduce.

The rest work fine! Great job with the fixes.

---

### Post by SeanHodges on 2009-12-20
Hey abhiroopb, hope you had a good holiday :)

> **abhiroopb said:**
> 1. Collection browser gave me the following error:
```

Failed to send query to remote machine
...

```
There is a bunch of other code below it but it is quite a lot to reproduce.

I haven't had chance to add many checks to the collection browser code yet. Can you make sure that the Tracker service is enabled on your PC? Right now the collection browser expects it will be available.

---

### Post by abhiroopb on 2009-12-20
Ah ok, I do usually keep tracker service disabled as it unnecessarily slows down my computer and I don't really use it anyway.

Anyway about the widget: the issue right now, as I mentioned is that there is no way to "minimise" the app while doing something else, e.g. checking gmail. I have to reconnect every time which takes some time.

But, I do agree that a widget is very battery heavy and it would mean keeping the process running in the background.

Right now all the important bugs seemed to be polished up. Great work!

---

### Post by SeanHodges on 2009-12-23
> **abhiroopb said:**
> Ah ok, I do usually keep tracker service disabled as it unnecessarily slows down my computer and I don't really use it anyway.

I did too :) You will need to enable it if you want to make use of the collection manager. It should still work fine if you set the lowest performance setting. I hope to add another search service in the future (like Beagle or Strigi), but for now Tracker is the only one supported.

> Anyway about the widget: the issue right now, as I mentioned is that there is no way to "minimise" the app while doing something else, e.g. checking gmail. I have to reconnect every time which takes some time.

But, I do agree that a widget is very battery heavy and it would mean keeping the process running in the background.

I have some ideas for this, but they'll probably have to wait until after the new year now. When I get chance I'll post them up on the android-tesla-devel mailing list. I've added a ticket to the bug tracker for the moment, feel free to add any comments if you like: [http://sourceforge.net/apps/trac/android-tesla/ticket/62](http://sourceforge.net/apps/trac/android-tesla/ticket/62)

---

### Post by abhiroopb on 2009-12-23
Ok I installed tracker (from synaptic) and started the trackerd service. 

The querying collection stayed on the screen for longer and then disappeared without finding the file I was looking for. I am assuming this is because tracker is still indexing. Will let you know (after about 3 hours) whether indexing worked or not.

Is tracker a bit like the mac spotlight? Where whatever I type in shows up, that would be quite useful actually...wouldn't mind using that. I could just never get it to work properly!

---

### Post by abhiroopb on 2009-12-24
The error no longer shows but when I search for a song (which I know exists) nothing shows up and the space below the search term is completely blank.

Thanks!

---

### Post by SeanHodges on 2009-12-24
> **abhiroopb said:**
> The error no longer shows but when I search for a song (which I know exists) nothing shows up and the space below the search term is completely blank.

Thanks!

Well first I would check that the problem is not just with Tesla. Open Applications -> Accessories -> Tracker Search Tool, and enter your search terms. Hopefully, your video/music should appear in the results window, which you can filter with the categories on the left. If this is the case, then we have a Tesla bug on our hands.

If not...

If this is the first time you've installed Tracker (sorry, I wrongly presumed it would already be installed on your system), then we may need to check the settings to make sure it's indexing the right stuff.

The first thing would be to do a quick sanity check. If you run **tracker-processes** from the command line, you should get back something similar to:

```
Found 202 pids...
Found process ID 4972 for 'trackerd'
Found process ID 4982 for 'tracker-applet'
Found process ID 5411 for 'tracker-indexer'
```

Then, if you open the tracker preferences utility (from the command-line it is called **tracker-preferences**). You should check that the following is set:

[LIST]
[*]General tab -> "Enabled indexing" ticked

[*]Files tab -> "Index and watch my home directory" ticked 
(or if your music/videos are in another directory/disk, specify that in the "Additional paths" box and set "Index mounted directories" as necessary).
[/LIST]

After that, you should be able to check the status of the indexer by running **tracker-status** and **tracker-stats** - the first one should tell you that Tracker is "Idle" when everything is up-to-date, and the second one should tell you how many files have been indexed. If the number of music and video files seems far too low, you may need to force a re-index by running the following command:

```
tracker-processes --hard-reset
/usr/lib/tracker/trackerd --force-reindex --verbosity=2
```

This should kick off a complete re-index in the foreground, telling you everything that's going on. Once the re-index finishes, you should be able to check the **tracker-stats** output again, and retry your search.

Really, none of this should be necessary, but if your Tracker is not working correctly then hopefully trying some of it might kick things into life.

---

### Post by abhiroopb on 2009-12-24
Song appears in tracker search tool fine (after indexing finished). Sorry to have to make you write everything out!

But, the error showed up again in Tesla

---

### Post by abhiroopb on 2009-12-29
The error does not show up in Tesla, but, the search does not reveal any results in Tesla. On the computer I can see the results of my search without a problem.

---

### Post by SeanHodges on 2009-12-29
Hey abhiroopb, thanks for the info.

I'll have a think about this, someone else is having the same problem as you, and I think the 2 problems are related somehow.

I'll add some extra checks into the next release (which will be pushed out over the next couple of days) and we'll see we get some indication of what's going wrong.

---

### Post by abhiroopb on 2009-12-29
> **SeanHodges said:**
> Hey abhiroopb, thanks for the info.

I'll have a think about this, someone else is having the same problem as you, and I think the 2 problems are related somehow.

I'll add some extra checks into the next release (which will be pushed out over the next couple of days) and we'll see we get some indication of what's going wrong.

Thanks.

Is it working fine for you?
Do you know others it is working for? I mean is it known to be buggy (other than myself and the other individual)?

---

### Post by SeanHodges on 2009-12-30
> **abhiroopb said:**
> Is it working fine for you?
Do you know others it is working for? I mean is it known to be buggy (other than myself and the other individual)?

It is working fine for me, on 2 separate machines (although I had to add trackerd to the start-up config on the PC running KDE4).

I'm not entirely sure why its not working for you at the moment, I'm hoping to get some useful error messages appear with the next release. So far only you and the guy who emailed me have reported any problems, but there are likely others who just haven't reported it.

When it's working, the collection browser is quite reliable, I think we just need to iron out some compatibility issues.

---

### Post by abhiroopb on 2010-01-18
Hi there!

I've been at work so haven't really been following. But how are things going?

---

### Post by SeanHodges on 2010-01-19
> **abhiroopb said:**
> Hi there!

I've been at work so haven't really been following. But how are things going?

Hey abhiroopb,

Well news-wise things have been quiet recently, but I have been busy. I'm looking at some fairly low-level Wifi connection issues at the moment. Hopefully some of my recent changes should keep a connection running for much longer than before (though the quality of the Wifi connnection is still an issue at the moment).

You'll be pleased to know I finally reproduced the issue you were having with Tracker. The problem was that some files were not reporting certain information that I was expecting. Strangely, I didn't see this issue for a long time. I downloaded some music that had this issue and all my queries started returning no results just like you had.

I'm hoping to do a release this week, but before I do that I want to run some tests against all the media players, like I did last time. I really want to avoid regressions from now on. I also want to test Tesla against my brand new Nexus One phone :)

I'll take a look at the state of the code tonight and see if I can do a quick build for you to test the Tracker fix...

---

### Post by abhiroopb on 2010-01-20
> **SeanHodges said:**
> Hey abhiroopb,

Well news-wise things have been quiet recently, but I have been busy. I'm looking at some fairly low-level Wifi connection issues at the moment. Hopefully some of my recent changes should keep a connection running for much longer than before (though the quality of the Wifi connnection is still an issue at the moment).

You'll be pleased to know I finally reproduced the issue you were having with Tracker. The problem was that some files were not reporting certain information that I was expecting. Strangely, I didn't see this issue for a long time. I downloaded some music that had this issue and all my queries started returning no results just like you had.

I'm hoping to do a release this week, but before I do that I want to run some tests against all the media players, like I did last time. I really want to avoid regressions from now on. I also want to test Tesla against my brand new Nexus One phone :)

I'll take a look at the state of the code tonight and see if I can do a quick build for you to test the Tracker fix...

Good to hear. Looking forward to the update!

---

### Post by Bakon Jarser on 2010-01-31
Hi Sean.

Looks like an interesting project and I'll be installing it once you make your next release.  I suggest you put a link to your page in your signature to make it easy for me and others to find. :)

---

### Post by SeanHodges on 2010-02-02
A very quick update (it's late) to let you know that I've just released the next version of Tesla!

Not particularly exciting feature-wise; but the service is not visible in the task bar, which adheres to the Android guidelines better and allows you to send Tesla to the background.

I've worked on some more fixes to improve the connection longevity, and the fixes I mentioned before are in there too.

Be sure to let me know how you get on with the update :)

---

### Post by abhiroopb on 2010-02-26
> **SeanHodges said:**
> A very quick update (it's late) to let you know that I've just released the next version of Tesla!

Not particularly exciting feature-wise; but the service is not visible in the task bar, which adheres to the Android guidelines better and allows you to send Tesla to the background.

I've worked on some more fixes to improve the connection longevity, and the fixes I mentioned before are in there too.

Be sure to let me know how you get on with the update :)

Sincere apologies for not getting back to you sooner.
About 2 weeks back I decided to buy a new desktop and owing to a number of factors (primary among them the fact that I was a bit disappointed with ATI’s lack of support for linux) I have started using Windows 7.

Before, I switched I did have an opportunity to try out your update and honestly there weren’t any problems. The fact that the app could run in the background was a big plus point and was an essential feature for me.

Anyway thanks a lot for bringing this app to my attention. For a very long time it was very helpful to my music listening needs and if I do switch back to Ubuntu (or dual boot) I will most certainly give this a try again.

Right now I am using [MediaMonkey]("http://www.mediamonkey.com/") as my music player and am planning on trying out [MonkeyTunes]("http://melloware.com/products/monkeytunes/") which appears to have a gorgeous interface!

---

### Post by SeanHodges on 2010-02-26
Hi abhiroopb,

Thanks for the final feedback, your help has been very valuable to the project. It will certainly be missed :)

Congratulations on the new desktop, it sounds like a very neat bit of kit. Windows 7 is a very good product too. Looking at your other thread, it sounds like you've found substitutes for all your software already! Hopefully over time a lot of the closed source programs can be replaced with open ones to help encourage a healthy technology ecosystem for the future.

Anyway, I'm working on a couple of other Android projects these days (though Tesla is by no means defunct). One of them is an on-line combat game (Android only for now), it's in the early stages but if you're interested I could keep you in the loop about it?

Will you be planning to visit this forum for much longer? Or is there a better way to contact you from now on (Twitter / Buzz / Email / etc)? I'd rather not sign up to a Windows 7 forum though, if it's all the same to you :)

Good luck with your Windows 7 gaming rig adventure! Perhaps one day Linux will once again find it's way back onto your desktop, when it better fits your purposes.

---

### Post by abhiroopb on 2010-02-26
have sent you a PM

---

### Post by flammenwurfer on 2010-04-16
I'm trying to get Tesla working with Amarok, but not having any luck.  I'm actually using Arch Linux and Amarok 2.3.0, but I couldn't find a website for Tesla to contact you.  

When I try to connect I get this error.

Post-connection tasks failed on remote machine
Init script filed with output: ConsoleKit session manager is not running

I haven't been able to use it yet, but it looks nice from what I've seen so far.

Edit:  I've also tried it with VLC and got the same error.

---

### Post by legolas_w on 2010-11-24
> **flammenwurfer said:**
> I'm trying to get Tesla working with Amarok, but not having any luck.  I'm actually using Arch Linux and Amarok 2.3.0, but I couldn't find a website for Tesla to contact you.  

When I try to connect I get this error.

Post-connection tasks failed on remote machine
Init script filed with output: ConsoleKit session manager is not running

I haven't been able to use it yet, but it looks nice from what I've seen so far.

Edit:  I've also tried it with VLC and got the same error.
Hi,

I have the same problem with Banshee, have you been able to fix it?

---

### Post by Ektor-5 on 2011-01-15
Same here on Arch Linux with Exaile.
I'm sure that is running (checked with ps aux and viewing logs)

What can I do???

-------
Ek5

---

