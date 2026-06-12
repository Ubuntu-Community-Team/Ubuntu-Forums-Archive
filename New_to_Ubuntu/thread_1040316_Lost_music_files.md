---
title: "Lost music files"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by gotanothergrot on 2009-01-15
I seem to have lost my song files, I have enclosed 3 screenshots to show why nothing showing in the last screen. This is the same with all the music files.

All my music is available in Amarok.

---

### Post by cariboo on 2009-01-15
I don't understand what you are saying, can you still play your tunes using Amarok? Or are they just listed in the database?

Jim

---

### Post by gotanothergrot on 2009-01-15
If for instance i open roger waters album amused to death, i do not see any songs from that album listed, nor from any album in the music file browser.

Have i done something to have caused this?

---

### Post by mjheagle8 on 2009-01-15
> **gotanothergrot said:**
> If for instance i open roger waters album amused to death, i do not see any songs from that album listed, nor from any album in the music file browser.

Have i done something to have caused this?

in amarok, can you play the files? or just see them? 
do you remember the name of your songs? bc you can try to find them if they moved by using ```
locate
``` and the name to find it.

---

### Post by gotanothergrot on 2009-01-15
Yes my music is listed in amarok and i can play them from there, what i want do be able to do is to find the songs in my files, so that i can send to another account or even email them.

---

### Post by gotanothergrot on 2009-01-15
Thanks for the replies, its late and i need to turn in now.

apart from the learning process linux and ubuntu are great so i will bear with it.

---

### Post by mjheagle8 on 2009-01-15
> **gotanothergrot said:**
> Yes my music is listed in amarok and i can play them from there, what i want do be able to do is to find the songs in my files, so that i can send to another account or even email them.

this means that the music indeed still exists on your computer. in amarok, right click on the song and look at the file properties. there will be a file path at the bottom, which will show you where it is located. repeat this as much as necessary and you will find out the location of all your music, where ever it is. hope this helps! tell me if you need additional clarification.

---

### Post by gotanothergrot on 2009-01-16
I have included a screensot the albums are listed in my home folder and the file path shows to that effect, thanks for the tip, but i want to be able to see the tracks listed in the file path.

---

### Post by redseventyseven on 2009-01-16
Perhaps they've been made as hidden files by mistake?

In Linux, any file whose filename begins with a "." is hidden. Try pressing Ctrl-H to reveal any hidden files in your music folders.

---

### Post by gotanothergrot on 2009-01-16
I did not see anything to suggest files are hidden, however the next screenshot shows the album highlighted as being empty.

---

### Post by gotanothergrot on 2009-01-16
All the files (albums) are empty.

---

### Post by redseventyseven on 2009-01-16
Did you actually press Ctrl-H to check?

Edit: here's another idea - can you start a terminal, copy & paste the following command, and then post the output:

```

ls '~/Music/Roger Waters/Amused to Death' -a

```

---

### Post by gotanothergrot on 2009-01-16
This is the output,

graham@coinshot:~$ ls '~/Music/Roger Waters/Amused to Death' -a
ls: cannot access ~/Music/Roger Waters/Amused to Death: No such file or directory
graham@coinshot:~$

---

### Post by mjheagle8 on 2009-01-16
> **gotanothergrot said:**
> This is the output,

graham@coinshot:~$ ls '~/Music/Roger Waters/Amused to Death' -a
ls: cannot access ~/Music/Roger Waters/Amused to Death: No such file or directory
graham@coinshot:~$

uh oh. its telling you the folder doesnt exist...

---

### Post by gotanothergrot on 2009-01-16
It did exist along with all the others, :???: 

Can i restore them from amarok?

---

### Post by gotanothergrot on 2009-01-16
OK I have just ripped a CD,James Morrison.

The tracks are listed OK as in the screen shot.

Thankfully I have the master copy of my Cd collection and i did not have a large collection on my hard drive.


Can anyone say why the original music files would just disappear but remain in Amarok?

Can i Purge my system to start over

---

### Post by mjheagle8 on 2009-01-16
> **gotanothergrot said:**
> It did exist along with all the others, :???: 

Can i restore them from amarok?

did you do what i suggested and find the file path in amarok? by viewing the song properties

---

### Post by Seq on 2009-01-17
If you are anything like me, and your screenshot looks like it, your music is a sizeable chunk of your data.

You could use "Disk Usage Analyzer" to help find it. If it is not installed, you will need to install 'baobab".

**Edit**: I should add, some music players (I am not familiar with amarok) move files to their own library location when imported. This is probably what mjheagle8 is working at.

---

### Post by fenian on 2009-01-17
The easiest non terminal way to find where your files were moved to is...

From the Places menu choose Search For Files

In the Name Contains field put .mp3 (or whatever format you use)

In the look in folder start with your Home directory then move on to any other partitions and check the File System as well,you should be able to find them this way.If they are playing in Amarok they are still somewhere on your computer.

---

### Post by mjheagle8 on 2009-01-17
if you can play it in amarok, you can view the file path in amarok, like i said!

---

### Post by gotanothergrot on 2009-01-17
> **mjheagle8 said:**
> if you can play it in amarok, you can view the file path in amarok, like i said!

I did the screen shot in amarok for the file path, it affirms the music is where it should be  but it is not.


I will do as fenian suggests next.

---

### Post by gotanothergrot on 2009-01-17
OK did the search and 136 missing files are found on my system, great but when i try to open in the location they are not there, see the shots i have included.

by the way i love this OS system despite a few things like this happening which makes me even more determined to get to the bottom of it, with the kind help from you lot of course.

---

### Post by nothingspecial on 2009-01-17
> **gotanothergrot said:**
> This is the output,

graham@coinshot:~$ ls '~/Music/Roger Waters/Amused to Death' -a
ls: cannot access ~/Music/Roger Waters/Amused to Death: No such file or directory
graham@coinshot:~$

It might work if you try ```
ls '~/Music/Rodger\ Waters/Amused\ to\ Death' -a
```

Bash doesn`t like spaces in Directory names. Notice the \ before any space.
Also bash is case sensitive. Is it Amused\ [COLOR="Red"]to[/COLOR]\ Death or Amused\ [COLOR="Red"]To[/COLOR]\ Death?

---

### Post by gotanothergrot on 2009-01-17
Here are the results.


graham@coinshot:~$ ls '~/Music/Rodger\ Waters/Amused\ to\ Death' -a
ls: cannot access ~/Music/Rodger\ Waters/Amused\ to\ Death: No such file or directory
graham@coinshot:~$

---

### Post by nothingspecial on 2009-01-17
This is weird.

Try navigating one directory at a time

```
cd Music
```

```
ls -a
```

can you see Rodger Waters?

If you can

```
cd Rodger\ Waters
```

little tip here you could probably just type cd Rod then press tab. Tab will finish it for you unless you`ve got and Rodger Whitaker.

```
ls -a

```

Is there anything there?

---

### Post by gotanothergrot on 2009-01-17
Its there, Great, what next...

 i am enjoying this, but alas i have to leave my computer for a few hours .....

graham@coinshot:~/Music$ ls -a
.                  Guru Josh Project               Pink Floyd
..                 Gym Class Heroes                Platnum
Alexandra Burke    Ida Maria                       P!nk
Alphabeat          Iglu & Hartly                   Razorlight
Basshunter         James Morrison                  Rihanna
Biffy Clyro        Jennifer Hudson                 Roger Waters
Blondie            Jordin Sparks                   Sash!
Boyzone            Kaiser Chiefs                   Snow Patrol
Chris Brown        Katy Perry                      Steve Mac
Chris Rea          Keane                           Sugababes
Christian Falk     Kid Rock                        Supermode - Tell My Why.mp3
Coldplay           Kings of Leon                   Taio Cruz
Dire Straits       Little Jackie                   The Police
Duffy              Madcon                          The Pussycat Dolls
Eric Prydz         Mark Knopfler                   The Saturdays
Flobots            Mark Knopfler & Emmylou Harris  The Script
Geraldine McQueen  McFly                           The Ting Tings
Girls Aloud        Ne-Yo                           The Verve
Grace Jones        Noah and the Whale              Will Young
graham@coinshot:~/Music$ cd Roger\ Waters
graham@coinshot:~/Music/Roger Waters$ ls -a
.  ..  Amused to Death
graham@coinshot:~/Music/Roger Waters$

---

### Post by arjuntank on 2009-01-17
try searching files from the deskbar applet
in case u dont get anything,
add the hidden files option from the drop down box

---

### Post by nothingspecial on 2009-01-17
Can you cd into Amused\ to\ Death does ls -a show the songs?

Also, just a thought, what happens if you try to copy Rodger Waters into another folder? Just use right click copy and paste.

*****Actually I don`t think the world is ready for another Rodger Waters but a few more Pussycat Dolls wouldn`t go amiss*****

---

### Post by gotanothergrot on 2009-01-17
I got this,

graham@coinshot:~$ cd Amused\to\Death
bash: cd: AmusedtoDeath: No such file or directory
graham@coinshot:~$ ls -a
.                        .gksu.lock            Public
..                       .gnome2               .pulse
2008                     .gnome2_private       .pulse-cookie
A                        .gnupg                .qt
.abuse                   .gphoto               R
.adobe                   .gpilotd              .recently-used
B                        .gpilotd.pid          .recently-used.xbel
.bash_history            .gstreamer-0.10       .registry
.bash_logout             .gtk-bookmarks        S
.bashrc                  .gvfs                 .screenlets
C                        .hplip                Screenshots
.cache                   I                     .ssh
.compiz                  .ICEauthority         .subversion
.config                  .icons                .sudo_as_admin_successful
.cups                    J                     .sword
D                        .java                 T
.DCOPserver_coinshot__0  K                     Templates
.DCOPserver_coinshot_:0  .kde                  .themes
Desktop                  L                     .thumbnails
.dmrc                    .local                thunderbird
Documents                .lyrics               .tomboy
.dvdcss                  M                     .tomboy.log
E                        .macromedia           .transmission
Email Attachments        .mcop                 trunk
.emerald                 .mcoprc               .update-manager-core
.esd_auth                .mozilla              .update-notifier
.evolution               .mozilla-thunderbird  V
Examples                 .mplayer              Videos
F                        Music                 .vlc
.fontconfig              N                     W
G                        .nautilus             .wapi
.gconf                   .openoffice.org2      .Xauthority
.gconfd                  P                     .xine
.ggz                     Pictures              .xscreensaver-getimage.cache
.gimp-2.4                .profile              .xsession-errors
graham@coinshot:~$

---

### Post by nothingspecial on 2009-01-17
You have to include the spaces, the \ just tells the terminal that a space is coming up and it`s ok. It`s not instead of a space.

```
cd Amused\ to\ Death
```

Also you have to do this from the Rodger Waters directory.

```
cd Music/Rodger\ Waters
```

```
cd Amused\ to\ Death
```

Then ```
ls -a
```

---

### Post by gotanothergrot on 2009-01-17
OK, this is what i got copying the code above


graham@coinshot:~$ cd Amused\ to\ Death
bash: cd: Amused to Death: No such file or directory
graham@coinshot:~$ cd Music/Rodger\ Waters
bash: cd: Music/Rodger Waters: No such file or directory
graham@coinshot:~$ cd Amused\ to\ Death
bash: cd: Amused to Death: No such file or directory
graham@coinshot:~$ ls -a
.                        .gksu.lock            Public
..                       .gnome2               .pulse
2008                     .gnome2_private       .pulse-cookie
A                        .gnupg                .qt
.abuse                   .gphoto               R
.adobe                   .gpilotd              .recently-used
B                        .gpilotd.pid          .recently-used.xbel
.bash_history            .gstreamer-0.10       .registry
.bash_logout             .gtk-bookmarks        S
.bashrc                  .gvfs                 .screenlets
C                        .hplip                Screenshots
.cache                   I                     .ssh
.compiz                  .ICEauthority         .subversion
.config                  .icons                .sudo_as_admin_successful
.cups                    J                     .sword
D                        .java                 T
.DCOPserver_coinshot__0  K                     Templates
.DCOPserver_coinshot_:0  .kde                  .themes
Desktop                  L                     .thumbnails
.dmrc                    .local                thunderbird
Documents                .lyrics               .tomboy
.dvdcss                  M                     .tomboy.log
E                        .macromedia           .transmission
Email Attachments        .mcop                 trunk
.emerald                 .mcoprc               .update-manager-core
.esd_auth                .mozilla              .update-notifier
.evolution               .mozilla-thunderbird  V
Examples                 .mplayer              Videos
F                        Music                 .vlc
.fontconfig              N                     W
G                        .nautilus             .wapi
.gconf                   .openoffice.org2      .Xauthority
.gconfd                  P                     .xine
.ggz                     Pictures              .xscreensaver-getimage.cache
.gimp-2.4                .profile              .xsession-errors
graham@coinshot:~$

---

### Post by Seq on 2009-01-17
How about just opening a terminal and running this:

```
find ~ -name *.mp3
```

Should show you every mp3 in your home folder

---

### Post by nothingspecial on 2009-01-17
Grok mate listen

When you open a terminal you open it in your home directory. You then have to navigate the file system. It will say there`s no directory called Rodger\ Waters because there isn`t. It`s in your music directory which is inside your home directory.

Your home
    |
  Music
    |
Rodger Waters
    |
Amused to Death

You have to navigate through the system either with one command using /

```
cd Music/Rodger\ Waters/Amused\ to\ Death
```

or one at a time like before.

---

### Post by Jorge_C on 2009-01-17
From the screenshots you posted, you should run
```
cd /Music/Roger\ Waters/Amused\ to\ Death/
``` (not Rodger)
and then
```
ls -a
```
in order to know which files are over there.

---

### Post by nothingspecial on 2009-01-17
My fault, theres no bloody d in Roger and there was I going on about typing stuff in correctly.

---

### Post by gotanothergrot on 2009-01-17
Is this weird

graham@coinshot:~$ cd /Music/Roger\ Waters/Amused\ to\ Death/
bash: cd: /Music/Roger Waters/Amused to Death/: No such file or directory
graham@coinshot:~$

---

### Post by gotanothergrot on 2009-01-17
would it be better to purge my music and start a new library?

---

### Post by Jorge_C on 2009-01-17
Let's do it step by step:
```
cd Music
```
```
ls -a
```

---

### Post by nothingspecial on 2009-01-17
> **gotanothergrot said:**
> would it be better to purge my music and start a new library?

It would be a pain and jorge didn`t miss a space. And yes it weird because when we navigated one directory at a time it was there,

---

### Post by gotanothergrot on 2009-01-17
graham@coinshot:~$ cd /music
bash: cd: /music: No such file or directory
graham@coinshot:~$

---

### Post by Jorge_C on 2009-01-17
Linux is case-sensitive, it's Music, not music.

---

### Post by nothingspecial on 2009-01-17
There`s no / before Music. Let me get this exactly right.
```

cd Music
```

```
ls -a
```

If you see Roger Waters

```
cd Roger\ Waters
```
```

ls -a
```

If you see Amused to Death (Is that how it`s spelled type exactly how it`s spelled in the output of ls- a with the \s)

```
cd Amused\ to\ Death
```

```
ls -a
```

Are there any music files

---

### Post by Jorge_C on 2009-01-17
You're right, nothingspecial. I edited my post to remove that mistake, thanks for pointing it out.

---

### Post by gotanothergrot on 2009-01-17
Thanks nothingspecial, heres the output.

graham@coinshot:~$ cd /music
bash: cd: /music: No such file or directory
graham@coinshot:~$ cd Music
graham@coinshot:~/Music$ ls -a
.                  Guru Josh Project               Pink Floyd
..                 Gym Class Heroes                Platnum
Alexandra Burke    Ida Maria                       P!nk
Alphabeat          Iglu & Hartly                   Razorlight
Basshunter         James Morrison                  Rihanna
Biffy Clyro        Jennifer Hudson                 Roger Waters
Blondie            Jordin Sparks                   Sash!
Boyzone            Kaiser Chiefs                   Snow Patrol
Chris Brown        Katy Perry                      Steve Mac
Chris Rea          Keane                           Sugababes
Christian Falk     Kid Rock                        Supermode - Tell My Why.mp3
Coldplay           Kings of Leon                   Taio Cruz
Dire Straits       Little Jackie                   The Police
Duffy              Madcon                          The Pussycat Dolls
Eric Prydz         Mark Knopfler                   The Saturdays
Flobots            Mark Knopfler & Emmylou Harris  The Script
Geraldine McQueen  McFly                           The Ting Tings
Girls Aloud        Ne-Yo                           The Verve
Grace Jones        Noah and the Whale              Will Young
graham@coinshot:~/Music$ cd Roger\ Waters
graham@coinshot:~/Music/Roger Waters$ ls -a
.  ..  Amused to Death
graham@coinshot:~/Music/Roger Waters$ cd Amused\ to\ Death
graham@coinshot:~/Music/Roger Waters/Amused to Death$ ls -a
.  ..
graham@coinshot:~/Music/Roger Waters/Amused to Death$

---

### Post by fenian on 2009-01-17
I noticed you have two other volumes (OS and Recovery) is it possible the music is in one of these?

If you run the following commands it should show all mp3 files in your home dirctory...

> cd /
find ~ -name *.mp3

If no mp3s are listed they must be in a different directory.

---

### Post by nothingspecial on 2009-01-17
Darn after all that there is nothing there yet they still play. This is so weird.

Well don`t delete anything in your music folder just yet. If it were me I`d rerip my cds to another folder, preserving the old one until you`ve done the new one.

Just out of interest if you have another media player - banshee or rhythmbox or something can you import Amused to Death into it?

To be honest I`m at a loss as to how amarok can play files that aren`t there, or for that matter where the stupid things have gone.

I`ll keep thinking on it though. At least you still have music to listen to. I once lost nearly 20,000 tunes, the thread`s on here somewhere.

I`ll get back if I can think of anything.

---

### Post by gotanothergrot on 2009-01-17
> **fenian said:**
> I noticed you have two other volumes (OS and Recovery) is it possible the music is in one of these?

If you run the following commands it should show all mp3 files in your home dirctory...



If no mp3s are listed they must be in a different directory.

Yes they are listed here.

---

### Post by nothingspecial on 2009-01-17
> **fenian said:**
> I noticed you have two other volumes (OS and Recovery) is it possible the music is in one of these?

If you run the following commands it should show all mp3 files in your home dirctory...



If no mp3s are listed they must be in a different directory.

Those commands will find any mp3 on your entire system, what`s the output?
Just one song will do you don`t have to post the lot.

It`s not shown the commands oh well, just so you know what I mean

```
cd /
```


```
find ~ -name *.mp3
```

---

### Post by gotanothergrot on 2009-01-17
I couldnt see roger in there so pasted the whole output

graham@coinshot:~$ cd /
graham@coinshot:/$ find ~ -name *.mp3
/home/graham/A/Alphabeat/Now That's What I Call Music! 71 (disc 2)/16 - Boyfriend (radio edit).mp3
/home/graham/A/Alexandra Burke/Hallelujah/03 - Without You.mp3
/home/graham/A/Alexandra Burke/Hallelujah/01 - Hallelujah.mp3
/home/graham/A/Alexandra Burke/Hallelujah/02 - Candyman.mp3
/home/graham/T/Ting Tings, The/Now That's What I Call Music! 71 (disc 2)/06 - Shut Up and Let Me Go.mp3
/home/graham/T/Taio Cruz/Now That's What I Call Music! 71 (disc 2)/21 - She's Like a Star (radio edit).mp3
/home/graham/I/Iglu & Hartly/Now That's What I Call Music! 71 (disc 2)/05 - In This City.mp3
/home/graham/I/Ida Maria/Now That's What I Call Music! 71 (disc 2)/18 - I Like You So Much Better When You're Naked.mp3
/home/graham/C/Chris Brown/Now That's What I Call Music! 71 (disc 1)/10 - Forever.mp3
/home/graham/C/Coldplay/Now That's What I Call Music! 71 (disc 2)/01 - Viva La Vida (radio edit).mp3
/home/graham/C/Christian Falk/Now That's What I Call Music! 71 (disc 2)/11 - Dream On (feat. Robyn) (radio edit).mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/16 - Gone Fishing.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/14 - Julia.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/08 - Josephine.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/03 - Auberge.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/04 - Let's Dance.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/09 - I Can Hear the Heartbeat.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/10 - The Road To Hell (Part 2).mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/15 - Looking For The Summer.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/07 - Tell Me There's A Heaven.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/06 - Nothing To Fear.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/05 - Stainsby Girls.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/01 - On The Beach.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/02 - Fool (If You Think It's Over).mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/11 - Winter Song.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/12 - God's Great Banana Skin.mp3
/home/graham/C/Chris Rea/Heartbeats - Chris Rea Greatest Hits/13 - You Can Go Your Own Way.mp3
/home/graham/P/Pussycat Dolls, The/Now That's What I Call Music! 71 (disc 1)/08 - When I Grow Up.mp3
/home/graham/P/P!nk/Now That's What I Call Music! 71 (disc 1)/03 - So What.mp3
/home/graham/P/Pink Floyd/The Division Bell/03 - Poles Apart.mp3
/home/graham/P/Pink Floyd/The Division Bell/04 - Marooned.mp3
/home/graham/P/Pink Floyd/The Division Bell/11 - High Hopes.mp3
/home/graham/P/Pink Floyd/The Division Bell/05 - A Great Day for Freedom.mp3
/home/graham/P/Pink Floyd/The Division Bell/07 - Take It Back.mp3
/home/graham/P/Pink Floyd/The Division Bell/10 - Lost for Words.mp3
/home/graham/P/Pink Floyd/The Division Bell/02 - What Do You Want From Me.mp3
/home/graham/P/Pink Floyd/The Division Bell/06 - Wearing the Inside Out.mp3
/home/graham/P/Pink Floyd/The Division Bell/08 - Coming Back to Life.mp3
/home/graham/P/Pink Floyd/The Division Bell/01 - Cluster One.mp3
/home/graham/P/Pink Floyd/The Division Bell/09 - Keep Talking.mp3
/home/graham/P/Pink Floyd/Wish You Were Here/04 - Wish You Were Here.mp3
/home/graham/P/Pink Floyd/Wish You Were Here/03 - Have a Cigar.mp3
/home/graham/P/Pink Floyd/Wish You Were Here/02 - Welcome to the Machine.mp3
/home/graham/P/Pink Floyd/Wish You Were Here/05 - Shine On You Crazy Diamond, Parts VI-IX.mp3
/home/graham/P/Pink Floyd/Wish You Were Here/01 - Shine On You Crazy Diamond, Parts I-V.mp3
/home/graham/P/Platnum/Now That's What I Call Music! 71 (disc 2)/22 - Love Shy (Thinking About You) (Virgo vs. Agent X edit).mp3
/home/graham/L/Little Jackie/Now That's What I Call Music! 71 (disc 2)/19 - The World Should Revolve Around Me.mp3
/home/graham/G/Girls Aloud/Now That's What I Call Music! 71 (disc 1)/01 - The Promise (single version).mp3
/home/graham/G/Geraldine McQueen/Now That's What I Call Music! 71 (disc 1)/15 - The Winners Song.mp3
/home/graham/G/Gym Class Heroes/Now That's What I Call Music! 71 (disc 2)/20 - Cookie Jar (feat. The Dream).mp3
/home/graham/G/Guru Josh Project/Now That's What I Call Music! 71 (disc 2)/10 - Infinity 2008 (Klaas vocal edit).mp3
/home/graham/B/Biffy Clyro/Now That's What I Call Music! 71 (disc 2)/17 - Mountains.mp3
/home/graham/B/Boyzone/Now That's What I Call Music! 71 (disc 1)/18 - Love You Anyway.mp3
/home/graham/B/Basshunter/Now That's What I Call Music! 71 (disc 1)/21 - Angel in the Night (radio edit).mp3
/home/graham/J/Jordin Sparks/Now That's What I Call Music! 71 (disc 1)/14 - Tattoo.mp3
/home/graham/J/Jennifer Hudson/Now That's What I Call Music! 71 (disc 1)/11 - Spotlight (UK radio edit).mp3
/home/graham/J/James Morrison/Now That's What I Call Music! 71 (disc 1)/12 - You Make It Real (radio version).mp3
/home/graham/V/Verve, The/Now That's What I Call Music! 71 (disc 2)/09 - Love Is Noise (radio edit).mp3
/home/graham/D/Duffy/Now That's What I Call Music! 71 (disc 2)/12 - Stepping Stone.mp3
/home/graham/F/Flobots/Now That's What I Call Music! 71 (disc 2)/13 - Handlebars (UK radio edit).mp3
/home/graham/K/Katy Perry/Now That's What I Call Music! 71 (disc 1)/02 - I Kissed a Girl.mp3
/home/graham/K/Katy Perry/Now That's What I Call Music! 71 (disc 1)/19 - Hot n Cold.mp3
/home/graham/K/Kid Rock/Now That's What I Call Music! 71 (disc 1)/05 - All Summer Long.mp3
/home/graham/K/Kaiser Chiefs/Now That's What I Call Music! 71 (disc 2)/07 - Never Miss a Beat.mp3
/home/graham/K/Kings of Leon/Now That's What I Call Music! 71 (disc 1)/04 - Sex on Fire.mp3
/home/graham/K/Keane/Now That's What I Call Music! 71 (disc 2)/14 - Spiralling (radio edit).mp3
/home/graham/N/Noah and the Whale/Now That's What I Call Music! 71 (disc 2)/04 - 5 Years Time.mp3
/home/graham/N/Ne-Yo/Now That's What I Call Music! 71 (disc 1)/07 - Miss Independent (album version).mp3
/home/graham/.local/share/Trash/files/01 - The Ballad of Bill Hubbard.mp3
/home/graham/S/Steve Mac/Now That's What I Call Music! 71 (disc 1)/23 - Paddy's Revenge (radio edit).mp3
/home/graham/S/Snow Patrol/Now That's What I Call Music! 71 (disc 2)/08 - Take Back the City.mp3
/home/graham/S/Snow Patrol/Eyes Open/13 - In My Arms.mp3
/home/graham/S/Snow Patrol/Eyes Open/05 - It's Beginning to Get to Me.mp3
/home/graham/S/Snow Patrol/Eyes Open/02 - Hands Open.mp3
/home/graham/S/Snow Patrol/Eyes Open/04 - Shut Your Eyes.mp3
/home/graham/S/Snow Patrol/Eyes Open/11 - The Finish Line.mp3
/home/graham/S/Snow Patrol/Eyes Open/01 - You're All I Have.mp3
/home/graham/S/Snow Patrol/Eyes Open/10 - Open Your Eyes.mp3
/home/graham/S/Snow Patrol/Eyes Open/09 - Headlights on Dark Roads.mp3
/home/graham/S/Snow Patrol/Eyes Open/14 - Warmer Climate.mp3
/home/graham/S/Snow Patrol/Eyes Open/03 - Chasing Cars.mp3
/home/graham/S/Snow Patrol/Eyes Open/06 - You Could Be Happy.mp3
/home/graham/S/Snow Patrol/Eyes Open/12 - -.mp3
/home/graham/S/Snow Patrol/Eyes Open/07 - Make This Go on Forever.mp3
/home/graham/S/Snow Patrol/Eyes Open/08 - Set the Fire to the Third Bar (feat. Martha Wainwright).mp3
/home/graham/S/Saturdays, The/Now That's What I Call Music! 71 (disc 1)/17 - Up (radio edit).mp3
/home/graham/S/Sugababes/Now That's What I Call Music! 71 (disc 1)/16 - Girls (radio edit).mp3
/home/graham/S/Sash!/Now That's What I Call Music! 71 (disc 1)/20 - Raindrops (Encore Une Fois) (feat. Stunt).mp3
/home/graham/S/Script, The/Now That's What I Call Music! 71 (disc 2)/02 - The Man Who Can't Be Moved.mp3
/home/graham/E/Eric Prydz/Now That's What I Call Music! 71 (disc 1)/22 - Pjanoo.mp3
/home/graham/M/McFly/Now That's What I Call Music! 71 (disc 2)/15 - Lies.mp3
/home/graham/M/Madcon/Now That's What I Call Music! 71 (disc 1)/09 - Beggin.mp3
/home/graham/W/Will Young/Now That's What I Call Music! 71 (disc 1)/13 - Changes.mp3
/home/graham/.mplayer/16 - Gone Fishing.mp3
/home/graham/.mplayer/14 - Julia.mp3
/home/graham/.mplayer/08 - Josephine.mp3
/home/graham/.mplayer/03 - Auberge.mp3
/home/graham/.mplayer/04 - Let's Dance.mp3
/home/graham/.mplayer/09 - I Can Hear the Heartbeat.mp3
/home/graham/.mplayer/10 - The Road To Hell (Part 2).mp3
/home/graham/.mplayer/15 - Looking For The Summer.mp3
/home/graham/.mplayer/07 - Tell Me There's A Heaven.mp3
/home/graham/.mplayer/06 - Nothing To Fear.mp3
/home/graham/.mplayer/05 - Stainsby Girls.mp3
/home/graham/.mplayer/01 - On The Beach.mp3
/home/graham/.mplayer/02 - Fool (If You Think It's Over).mp3
/home/graham/.mplayer/11 - Winter Song.mp3
/home/graham/.mplayer/12 - God's Great Banana Skin.mp3
/home/graham/.mplayer/13 - You Can Go Your Own Way.mp3
/home/graham/R/Razorlight/Now That's What I Call Music! 71 (disc 2)/03 - Wire to Wire.mp3
/home/graham/R/Rihanna/Now That's What I Call Music! 71 (disc 1)/06 - Disturbia (album version).mp3
/home/graham/R/Roger Waters/Amused to Death/10 - What God Wants, Part III.mp3
/home/graham/R/Roger Waters/Amused to Death/09 - What God Wants, Part II.mp3
/home/graham/R/Roger Waters/Amused to Death/04 - Perfect Sense, Part II.mp3
/home/graham/R/Roger Waters/Amused to Death/05 - The Bravery of Being Out of Range.mp3
/home/graham/R/Roger Waters/Amused to Death/07 - Late Home Tonight, Part II.mp3
/home/graham/R/Roger Waters/Amused to Death/02 - What God Wants, Part I.mp3
/home/graham/R/Roger Waters/Amused to Death/08 - Too Much Rope.mp3
/home/graham/R/Roger Waters/Amused to Death/13 - It's a Miracle.mp3
/home/graham/R/Roger Waters/Amused to Death/11 - Watching TV.mp3
/home/graham/R/Roger Waters/Amused to Death/06 - Late Home Tonight, Part I.mp3
/home/graham/R/Roger Waters/Amused to Death/12 - Three Wishes.mp3
/home/graham/R/Roger Waters/Amused to Death/03 - Perfect Sense, Part I.mp3
/home/graham/R/Roger Waters/Amused to Death/14 - Amused to Death.mp3
/home/graham/Music/Mark Knopfler/The Best of Dire Straits & Mark Knopfler: Private Investigations/12 - Boom, Like That.mp3
/home/graham/Music/Mark Knopfler/The Best of Dire Straits & Mark Knopfler: Private Investigations/11 - Why Aye Man.mp3
/home/graham/Music/Mark Knopfler/The Best of Dire Straits & Mark Knopfler: Private Investigations/10 - Going Home (Theme From Local Hero).mp3
/home/graham/Music/Mark Knopfler/The Best of Dire Straits & Mark Knopfler: Private Investigations/13 - What It Is.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/07 - Brothers in Arms.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/09 - On Every Street.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/03 - Romeo & Juliet.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/05 - Private Investigations.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/06 - Money for Nothing.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/02 - Love Over Gold.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/08 - Walk of Life.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/01 - Sultans of Swing.mp3
/home/graham/Music/Dire Straits/The Best of Dire Straits & Mark Knopfler: Private Investigations/04 - Tunnel of Love.mp3
/home/graham/Music/Mark Knopfler & Emmylou Harris/The Best of Dire Straits & Mark Knopfler: Private Investigations/14 - All the Roadrunning.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 06 - Undiscovered.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 13 - Better Man.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 08 - Call the Police.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 07 - The Letter.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 10 - If the Rain Must Fall.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 05 - One Last Chance.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 09 - This Boy.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 01 - Under the Influence.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 03 - Wonderful World.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 12 - The Last Goodbye.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 04 - The Pieces Don't Fit Anymore.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 02 - You Give Me Something.mp3
/home/graham/Music/James Morrison/James Morrison - Undiscovered/James Morrison (Undiscovered) - 11 - How Come.mp3
/home/graham/Music/Supermode - Tell My Why.mp3
graham@coinshot:/$

---

### Post by gotanothergrot on 2009-01-17
I can see him now

---

### Post by mjheagle8 on 2009-01-17
there's your files. they're in /home/graham/ the letter of the artist/ etc...

---

### Post by nothingspecial on 2009-01-17
Well there all there and it is possible to move them back if you want to.
A few commands should do it although you`ve gotta type em right. Do you want to?

---

### Post by fenian on 2009-01-17
These commands will move all the files back into the Music folder...

> mv /home/graham/A/ /home/graham/Music/

mv /home/graham/T/ /home/graham/Music/

mv /home/graham/C/ /home/graham/Music/

mv /home/graham/I/ /home/graham/Music/

mv /home/graham/P/ /home/graham/Music/

mv /home/graham/L/ /home/graham/Music/

mv /home/graham/G/ /home/graham/Music/

mv /home/graham/B/ /home/graham/Music/

mv /home/graham/J/ /home/graham/Music/

mv /home/graham/V/ /home/graham/Music/

mv /home/graham/K/ /home/graham/Music/

mv /home/graham/S/ /home/graham/Music/

mv /home/graham/.mplayer/*.mp3 /home/graham/Music/

mv /home/graham/R/ /home/graham/Music/

---

### Post by nothingspecial on 2009-01-17
In fact it might be easier just copy and paste if that`s all of them.

Anyway, I`m glad you`ve found them. That would have bugged me for ages.

---

### Post by gotanothergrot on 2009-01-17
> **fenian said:**
> These commands will move all the files back into the Music folder...

fenian, shall copy and that lot in the terminal?

---

### Post by gotanothergrot on 2009-01-17
> **nothingspecial said:**
> Well there all there and it is possible to move them back if you want to.
A few commands should do it although you`ve gotta type em right. Do you want to?

Yes.

---

### Post by fenian on 2009-01-17
Copy and paste those lines one by one ,check after the first line to make certain the files moved correctly.

---

### Post by nothingspecial on 2009-01-17
Those commands will give you an A B C etc directory in your Music folder. If your happy with that then go ahead. Although you will still have the empty original files. Also all your Now that`s what I call music files wont be in a now.... file they`ll be all over.

---

### Post by gotanothergrot on 2009-01-17
This is where one has to be patient!!!

first line =


graham@coinshot:~$ mv /home/graham/A/ /home/graham/Music/
mv: cannot stat `/home/graham/A/': No such file or directory
graham@coinshot:~$

---

### Post by fenian on 2009-01-17
It may just be easier to open your home directory and drag the "A" folder into the Music folder.

---

### Post by gotanothergrot on 2009-01-17
Thanks fenian i am almost there, i think, this is where im at shall i proceed??

---

### Post by fenian on 2009-01-17
Yes select  merge.

---

### Post by gotanothergrot on 2009-01-17
Yes they are going in, Praise be, i had a couple of errors but may i heartily thank you guys for helping me thus far.

Where do i find thank and solved buttons??

---

### Post by nothingspecial on 2009-01-17
Solved is in the thread tools.

Thanks has gone.

Glad you`ve got it sorted and also (I Hope) you`ve learned a bit about navigating the linux file system.

---

### Post by gotanothergrot on 2009-01-17
I have,, i would hope to get to know the system like you guys i rarely visit windows now i am glad i took the plunge. Special thanks to all

---

### Post by gotanothergrot on 2009-01-17
> **nothingspecial said:**
> Solved is in the thread tools.

Thanks has gone.

Glad you`ve got it sorted and also (I Hope) you`ve learned a bit about navigating the linux file system.


I can't see it.

---

### Post by fenian on 2009-01-17
They tookk the thanks and solved options out due to the recent database problems on the forums.

---

### Post by mjheagle8 on 2009-01-17
> **fenian said:**
> They tookk the thanks and solved options out due to the recent database problems on the forums.

is it coming back?

---

