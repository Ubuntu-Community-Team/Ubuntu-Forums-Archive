---
title: "How to stop banshee???!!!"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by beew on 2011-05-07
WTF?! There is no stop button in Banshee for 11.04? (only pause, backward and forward) Even closing the app the music continues to play.

It is just amazing that do such a sloppy job in a final release.

---

### Post by tgm4883 on 2011-05-07
> **beew said:**
> WTF?! There is no stop button in Banshee for 11.04? (only pause, backward and forward) Even closing the app the music continues to play.

It is just amazing that do such a sloppy job in a final release.

What is the point in stopping vs pausing?

---

### Post by beew on 2011-05-07
> **tgm4883 said:**
> What is the point in stopping vs pausing?

Pausing means it is still running, if you click it it picks up where it left off. Stopping as in kill, stop, no more. I can stop it with quit in 10.10. But there is no quit in 11.04 and as I said, even closing the app doesn't kill it.

Yes, I know how to kill it from the terminal, but is this expected behaviour for the default music player?

---

### Post by Elfy on 2011-05-07
> **tgm4883 said:**
> What is the point in stopping vs pausing?

What is the point in only pausing?

Edit - just seems like really odd behaviour to me in truth.

---

### Post by nerdy_kid on 2011-05-07
you can stop it from the terminal via "banshee --stop"

Other then that, you can edit the Unity quicklist: [http://www.omgubuntu.co.uk/2011/04/how-to-add-a-banshee-quicklist-for-easy-music-control-in/](http://www.omgubuntu.co.uk/2011/04/how-to-add-a-banshee-quicklist-for-easy-music-control-in/)

Why does it matter though?  Unless you don't have a lot of ram, I can't see the point in needing banshee quited/stopped.

---

### Post by beew on 2011-05-07
> **nerdy_kid said:**
> you can stop it from the terminal via "banshee --stop"

Other then that, you can edit the Unity quicklist: [http://www.omgubuntu.co.uk/2011/04/how-to-add-a-banshee-quicklist-for-easy-music-control-in/](http://www.omgubuntu.co.uk/2011/04/how-to-add-a-banshee-quicklist-for-easy-music-control-in/)

Why does it matter though?  Unless you don't have a lot of ram, I can't see the point in needing banshee quited/stopped.

I know how to stop it from the terminal, but what kind of music player that doesn't have a built in stop button? That is pretty bad.

Thanks for the link, but it is ridiculous all the same that you have to go to third party tweaks (or any tweak at all ) for something so basic and banshee is the default media player, not some weirdo app I installed myself!

---

### Post by tgm4883 on 2011-05-07
> **forestpiskie said:**
> What is the point in only pausing?

Edit - just seems like really odd behaviour to me in truth.

Actually, it seems like streamlining to me. Isn't the job of a stop button is to stop the music from playing. Isn't that what a pause button does as well? Why have two buttons for the same job?


@OP - Not trying to be funny here, but do you actually like anything?

---

### Post by Paqman on 2011-05-07
> **tgm4883 said:**
> Actually, it seems like streamlining to me. Isn't the job of a stop button is to stop the music from playing. Isn't that what a pause button does as well? Why have two buttons for the same job?


Exactly, having a separate stop and pause button is a hangover from physical media. There's no reason for a digital music player to have two buttons.

---

### Post by ajgreeny on 2011-05-07
@OP

I don't think there has ever been a separate STOP button in banshee, as far as I remember.  I still run 10.04 and that just has a pause and play button which toggles between the two, depending on whether you are already in play or pause mode.

I don't see the problem!

Have you looked at rhythmbox in previous ubuntu versions?  That doesn't have a stop button either.

---

### Post by beew on 2011-05-07
> **ajgreeny said:**
> @OP

I don't think there has ever been a separate STOP button in banshee, as far as I remember.  I still run 10.04 and that just has a pause and play button which toggles between the two, depending on whether you are already in play or pause mode.

I don't see the problem!

Have you looked at rhythmbox in previous ubuntu versions?  That doesn't have a stop button either.

Banshee in 10.10 has a quit option under media. It is really odd behaviour that you cannot kill the music even by closing the application.

---

### Post by beew on 2011-05-07
> **tgm4883 said:**
> Actually, it seems like streamlining to me. Isn't the job of a stop button is to stop the music from playing. Isn't that what a pause button does as well? Why have two buttons for the same job?


@OP - Not trying to be funny here, but do you actually like anything?

I have explained the difference. In VLC for example there are both pause and stop. Stop means fin, done, clean, kill. Pause means you can resume, it is not finished.

How much "streamlining" you ge by saving one button?

I like many things except smart a**es who are not being helpful but feel like posting anyway.

---

### Post by Jesus_Valdez on 2011-05-07
Do you want to kill banshee or to make it stop? To me sounds like two different things.

Anyway what I do is I pause the reproduction and then ctrl + q or simply select quit from the menu.

---

### Post by beew on 2011-05-07
> **Jesus_Valdez said:**
> Do you want to kill banshee or to make it stop? To me sounds like two different things.

Anyway what I do is I pause the reproduction and then ctrl + q or simply select quit from the menu.

There is no quit in the menu for 11.04. That is my whole point. Choose "close" doesn't stop it, only closes the gui.

---

### Post by sevoxx on 2011-05-07
Press pause. Problem solved.

---

### Post by Paqman on 2011-05-07
> **beew said:**
> There is no quit in the menu for 11.04. That is my whole point. Choose "close" doesn't stop it, only closes the gui.

If you close Banshee while the music is paused, it quits. If you close it while it's playing, it keeps playing. Ctrl-W or clicking "quit" in the Unity launcher also works IIRC.

---

### Post by ajgreeny on 2011-05-07
> **beew said:**
> There is no quit in the menu for 11.04. That is my whole point. Choose "close" doesn't stop it, only closes the gui.
But you did not say there was no "Quit" in the Media menu when you wrote your original post, just that there was no "Stop";  they are two very different things, hence our confusions when answering.

Now you explain in more detail, I have to agree with you.  As I said, I am still running 10.04, so was not aware that there is no way to properly close/exit banshee as opposed to pausing it.

Yet one more reason to avoid 11,04, I think!

---

### Post by beew on 2011-05-07
So it was considered a bug and fixed back in Jan, maybe something breaks again.

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/706746](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/706746)

So if it was  treated as a bug then it certainly is still a bug when it occurs now. So much for the people who try to argue that it is a "streamlining" feature that you have no quit/stop option.

---

### Post by beew on 2011-05-07
The quit option in the Unity launcher doesn't quit banshee, it only quits the gui.


Pause then close works. But this is just weird.

---

### Post by Paqman on 2011-05-07
> **beew said:**
> 
So if it was  treated as a bug then it certainly is still a bug when it occurs now. So much for the people who try to argue that it is a "streamlining" feature that you have no quit/stop option.

They have changed the behaviour of Banshee. If you close it when it's not playing, it quits.

The bug was filed because at one point in Natty development this was broken. It is now fixed.

---

### Post by Jesus_Valdez on 2011-05-07
Probably I have a different version because I see a Quit option.

Anyway, ctrl + q quits the application if the music is paused.

There used to be a extension controlling the access of Banshee to the Music Menu, you could look for it and deactivating. 

Also, there is very easy to choose another media player if you are not happy with banshee.

You could use some of your complaining effort in choosing another one, I recommend mpd or guayadeque.

---

### Post by beew on 2011-05-07
> **Jesus_Valdez said:**
> 
You could use some of your complaining effort in choosing another one, I recommend mpd or guayadeque.

Yeah I know that, but I want to try out Banshee and apart from this I don't dislike it. 

In fact I use VLC as my main music player that's why I didn't even notice this before.

---

### Post by uRock on 2011-05-07
Why recommend using another program instead of fixing the one which is the default music player? One shouldn't have to pause music to quit the player.

I do wonder why Canonical chose Banshee over Rhythmbox.

---

### Post by mc4man on 2011-05-07
> **beew said:**
> So it was considered a bug and fixed back in Jan, maybe something breaks again.

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/706746](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/706746)

So if it was  treated as a bug then it certainly is still a bug when it occurs now. So much for the people who try to argue that it is a "streamlining" feature that you have no quit/stop option.

The 'bug' was that banshee was not closing w/ no track playing

The current behavior of banshee is what is expected of any app using the sound pref's menu

Edit: - some perspective - maybe
min button - minimizes to window list or launcher whether playing or not
close button, close command, quit entry in launcher - if not playing  exits/closes the player
if playing -  minimizes player to the sound menu _only,_ icon disappears from launcher if not pinned

---

### Post by tgm4883 on 2011-05-07
> **beew said:**
> I have explained the difference. In VLC for example there are both pause and stop. Stop means fin, done, clean, kill. Pause means you can resume, it is not finished.


I think I explained this before, if both options job is to stop the music from playing then I think pause makes more sense and you don't need to buttons to do the same thing. Reading some of your other posts here it seems the real issue is that you cannot close banshee. That is an entirely different problem.

> **beew said:**
> 
How much "streamlining" you ge by saving one button?


A lot. In a menu that only has 4-5 entries cutting it down by one is cutting down quite a bit of clutter. 

> **beew said:**
> 
I like many things except smart a**es who are not being helpful but feel like posting anyway.

Yea, I kinda expected you to respond that way. I've seen a few of your posts before in other threads which is why I asked that question. I wasn't trying to be a smartass, it was a legit question since you seem like a pretty negative person. But whatever. To quote one of my favorite internet shows, die in a fire.

---

### Post by paulocr on 2011-06-26
When you close the banshee window the playback is meant to be controlled from the sound menu in ubuntu.
You can return to the regular player behavior if you disable the sound integration from the extensions option in banshee.
Once you do that once you close the player window the playback will stop.

---

### Post by trekguy on 2011-06-27
> **paulocr said:**
> When you close the banshee window the playback is meant to be controlled from the sound menu in ubuntu.
You can return to the regular player behavior if you [B]disable the sound integration from the extensions option in banshee.
Once you do that once you close the player window the playback will stop[/B].

Perfect... thank you!

---

### Post by dchky on 2011-07-01
> **sevoxx said:**
> Press pause. Problem solved.

Forgive my response, but that is an idiotic solution - when I click "Close" I expect the application process to be killed, end of story. If I wanted to hide it and continue playing, I'd put it on a different virtual desktop or simply minimize it.

Banshee, yet another audio player I tried for 3 minutes and found it utterly lacking in basic UI concepts.

> When you close the banshee window the playback is meant to be controlled from the sound menu in ubuntu.
You can return to the regular player behavior if you disable the sound integration from the extensions option in banshee.
Once you do that once you close the player window the playback will stop.

Great, so now I get yet another icon in the notification area - this is one annoyance for another.

---

### Post by computerandu on 2011-07-01
> **beew said:**
> The quit option in the Unity launcher doesn't quit banshee, it only quits the gui.


Pause then close works. But this is just weird.

I agree with beew....

And I do not understand why people are suggesting to get away with pausing it...
for me pausing is not equal to stopping
it is like the difference between ctrl+c and ctrl+z to a process...
even if it is paused it does consume memory...why would i waste memory on that?

---

### Post by computerandu on 2011-07-01
> **dchky said:**
> Forgive my response, but that is an idiotic solution - when I click "Close" I expect the application process to be killed, end of story. If I wanted to hide it and continue playing, I'd put it on a different virtual desktop or simply minimize it.

Banshee, yet another audio player I tried for 3 minutes and found it utterly lacking in basic UI concepts.



Great, so now I get yet another icon in the notification area - this is one annoyance for another.

right on the spot...my views exactly...

---

### Post by tgm4883 on 2011-07-01
> **computerandu said:**
> right on the spot...my views exactly...

It sounds like there are two different issues being discussed in this thread.

1) Not having a button called Stop to stop music from playing, but keeping Banshee open. (This is what I've discussed previously)

2) Hitting the close button on Banshee and Banshee not shutting down.

I haven't seen 2, but if that is true that sounds like a legit issue.

For 1, the isn't really a difference between Stopping and Pausing.

---

### Post by egalvan on 2011-07-02
> **tgm4883 said:**
> It sounds like there are two different issues being discussed in this thread.
This is true, and probably caused some confusion.

> 2) Hitting the close button on Banshee and Banshee not shutting down.
This behavior is shown by many apps, but usually has an option to configure to the user's liking.

> For 1, the isn't really a **difference between Stopping and Pausing**.

"pause" implies that something may start again in a short span of time.
"stop" implies that something is "done with", "over", "will not start again soon"

for example...
a symphony "pauses" between movements, but "stops" at the end.

a play "pauses" between /scenes/acts, but "stops" at the end.

if I'm listening to music and the phone rings, I want to "pause" the music with the intention of starting again after the conversation ends.
If the phone call is to inform me I've won the Lottery, then I want the music to stop, because I will be leaving my computer to pick up my winnings, and I don't know when I will start that song again  :)

And one last one...
do you want your heart to  "pause" or "stop" ?

---

### Post by tgm4883 on 2011-07-02
> **egalvan said:**
> This is true, and probably caused some confusion.


This behavior is shown by many apps, but usually has an option to configure to the user's liking.



"pause" implies that something may start again in a short span of time.
"stop" implies that something is "done with", "over", "will not start again soon"

for example...
a symphony "pauses" between movements, but "stops" at the end.

a play "pauses" between /scenes/acts, but "stops" at the end.

if I'm listening to music and the phone rings, I want to "pause" the music with the intention of starting again after the conversation ends.
If the phone call is to inform me I've won the Lottery, then I want the music to stop, because I will be leaving my computer to pick up my winnings, and I don't know when I will start that song again  :)

And one last one...
do you want your heart to  "pause" or "stop" ?

Wow, that's.... nm.

The point of stop in a music player is to stop music from playing. The point of pause in a music player is to stop music from playing. 

From a system resources standpoint, depending on how the application is coded there is zero difference.

From a functional standpoint, there are a few options.

1) You want music to stop playing, and to resume from the same point you were at (so hit the pause button to stop, then hit pause again to start).

2) You want the music to stop playing and when you want it to start again you want it to start from the beginning of the same song (so hit pause button to stop, then the track back button ( |<- ))

3) You want the music to stop playing and when you want it to start again you want it to start from the next song (so hit pause button to stop, then the track next button ( ->| ))

Length of time the music stops has no bearing. 

So why do I need a stop button again?

---

### Post by thane1 on 2011-07-02
This isn't exclusive to banshee.  Rhythmbox works the same way, at least in 10.10 - and its really irritating.  Normal convention suggests, that pause means temporarily cease - to be resumed.  Stop means cease for good.  Shouldn't be a major problem to make the programs work logically as per the menus.  In rhythmbox I also need to press pause and then close the window.  Not intuitive at all.  Just my opinion as constructive criticism for the betterment of all.  cheers

---

### Post by egalvan on 2011-07-03
> **tgm4883 said:**
> 

So why do I need a stop button again?

**YOU** may not want or need a stop button, but why impose your wants and needs upon others?
After all, if it's there, you can ignore it...
but if it's NOT there, its impossible to use it if one wants or needs it, or is used to it.

To me, stop and pause have different meanings and uses...

One reason I use Microsoft to play my music and videos is that I haven't found software under GNU/Linux that work as **I** want... or am used to...

One day, perhaps it will appear...

---

### Post by skimtneer on 2011-07-21
> **paulocr said:**
> When you close the banshee window the playback is meant to be controlled from the sound menu in ubuntu.
You can return to the regular player behavior if you disable the sound integration from the extensions option in banshee.
Once you do that once you close the player window the playback will stop.

I'm pretty sure this is all that anyone was asking for in this thread, from the original poster to all the rest.  No one's asking for a "stop the music" button on the banshee controls, as if they want to make it like a retro-style copy of an old physical cassette tape player.  NO.  They're only asking for the "close the app window button" to actually kill the app, which should be expected behavior for pretty much any app on a GUI.

I like the "sound integration" option with the ability to control banshee from the toolbar, but if it means the "close the window" button doesn't stop playback, forget it.  It's pretty dumb to have to click in two different places to get sound to stop AND the app to close.  I guess I'll disable the integration and just forfeit the nice toolbar control.

---

### Post by skimtneer on 2011-07-21
Incidentally, it was not Sound Menu Integration which I had to disable to stop the "zombie" behavior of Banshee.  That was already unchecked in my Preferences > Extensions menu.  Instead I had to uncheck "Notification Area Icon".

Those two options seem to be somewhat overlapping with each other, which is another strange UI quirk.  I'm not sure why it would be desirable to be able to control the player both with right-click from the sound menu (little speaker/volume icon on the taskbar) and also from a dedicated banshee icon right next to it on the sound bar.  Why two options that are almost identical?  They both can start, pause, and jump tracks.  The only thing the dedicated banshee control appears to do which the "right click on the volume icon" control does not, is show a bit larger thumbnail of the album cover.

---

### Post by moorecf on 2011-07-30
I cannot stop Banshee in 11.04 either.   My music file is on an external hard drive.   I want to stop the music and "Safely Remove Drive".   A message pops up "Cannot stop'......

---

### Post by scorchgeek on 2011-07-30
I'm surprised that in four pages nobody mentioned the Playback --> Stop when Finished option (Shift-Space), which will play a track to the end and then "stop", i.e. clicking Play will restart the track to the beginning. Granted, it's not exactly the same as a stop button, but it at least has "stop" in the name and isn't a pause button.

---

### Post by Justfax on 2011-08-17
Wow - amazing how a simple problem can be complicated into something much bigger - I think we all know the difference between the actions of 'Pause' and 'Stop' thank you.
I agree with the original poster, if you start playing an audio track and then close the banshee app without pausing the track banshee will continue to play the track and the only way to stop it is to stop the banshee service via a terminal command or to mute/turn off your speakers.  If, in addition you start another media app, VLC to play a video for example, you get 2 sound tracks !
Now - how can that be right ?  Just provide a stop button and the problem goes away.

---

### Post by Paqman on 2011-08-17
> **Justfax said:**
> the only way to stop it is to stop the banshee service via a terminal command or to mute/turn off your speakers.

No, you can simply re-open Banshee and hit pause, then close Banshee.

---

### Post by jprobe on 2011-08-17
> How to stop [a] banshee?You *can't* stop a banshee.

---

