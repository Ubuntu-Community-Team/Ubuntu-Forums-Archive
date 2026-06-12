---
title: "i need help fast its an emergency"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by ru236 on 2009-10-02
i need help please my movie player wont work it says that i need dvd plugins but when i search for that it says that packages for plugin not found so my movie wont play and now it wont even keep open ill try play the movie and it will open but then it just dies closes so can anyone help me or recomend me a better movie player

---

### Post by esters on 2009-10-02
MPlayer or VLC

Before that check - [http://www.medibuntu.org/](http://www.medibuntu.org/) (That should resolve the DVD decoder/plugin problem)

---

### Post by Jason Cook on 2009-10-02
I would recomend that you use VLC. It has many built in plugins.

---

### Post by tacantara on 2009-10-02
Have you tried installing ubuntu-restricted-extras from Synaptic?  That may take care of your video issues.

---

### Post by ru236 on 2009-10-02
how do i get vlc

---

### Post by ru236 on 2009-10-02
do i add the repository under how to reposotory

---

### Post by Shibblet on 2009-10-02
First type in Terminal...

```
sudo apt-get install libdvdcss2
```

That will add your DVD Decoder.

> **ru236 said:**
> how do i get vlc

It's in Add/Remove programs...

---

### Post by ru236 on 2009-10-02
i already did that sudo libdvdcss2 deal

---

### Post by NinjaNumberNine on 2009-10-02
> **ru236 said:**
> i need help please my movie player wont work it says that i need dvd plugins but when i search for that it says that packages for plugin not found so my movie wont play and now it wont even keep open ill try play the movie and it will open but then it just dies closes so can anyone help me or recomend me a better movie player
Congrats, dude. You totally got our attention. HOWEVER: please don't post such boy-who-cried-wolf titles on smaller things, (which, admittingly, yours was) because if someone really does have a problem, people may think "i see those all the time." Personally I recommend kplayer if you use kubuntu (or kde), or Totem if you use Ubuntu (or gnome.) As for the "no suitable plugins found, maybe you need to go in Add/Remove Programs and choose "all opensource software" (or similar, I can't remember exactly)  in the top dropdown menu. Then search "gstreamer" and install all the codecs there. Next, search "ubuntu" and install "Ubuntu restricted extras". Then, go in terminal, type "sudo apt-get install libdvdcss2" and press enter. If it says something about the package not being found, try "sudo apt-get install libdvdcss". 

 Hope it helps,



NinjaNumberNine




EDIT: I see you have done some of that already. Skip everything in my instructions that you have already done. BTW is it an encrypted DVD? If so, then thats what libdvdcss2 is for.

---

### Post by ru236 on 2009-10-02
well it was the only way i could get help cuz ive been at this for a while im new to this ubuntu thing so im still trying it out

---

### Post by NinjaNumberNine on 2009-10-02
-No sweat, I done it lots of times when I was a little guy. :lol: (little in wisdom, but big in heart) Anyway, it comes naturally to correct someone, ESPECIALLY if you do it to- that's how you know it's wrong...

"Grace for me and Justice for you"
-My Motto

(:lol:  just kidding lol)

---

### Post by Paddy Landau on 2009-10-02
> **ru236 said:**
> well it was the only way i could get help cuz ive been at this for a while im new to this ubuntu thing so im still trying it out
The only way? I've posted many threads asking for help, and they were all answered. Without pretending it was an emergency. Please remember that people on this forum are unpaid volunteers -- as I hope you, too, one day, will be.

---

### Post by starcannon on 2009-10-02
> **ru236 said:**
> well it was the only way i could get help cuz ive been at this for a while im new to this ubuntu thing so im still trying it out
I hope you don't end up needing to retrieve a deleted file that is due for some real life emergency at some point. I think after sounding the alarm over watching movies, you may have a hard time convincing people to run and look.

Sometimes it takes a while to get sorted; everyone here is a volunteer, you just did the equivalent of pushing your way to the front of the line. The best thing to do is post your question, keep an eye on your thread, and bump it to the top once a day; and, while your waiting google like mad, believe it or not your particular "emergency" has entire tutorials written up on various web pages across the internet. If somehow you don't find the answer while your waiting for someone to get to you, you will find, that you will get answered as long as you bump to the top once a day.

GL and HF

---

### Post by scratman on 2009-10-02
Open Terminal and paste all of this into it:-

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar gnome-mplayer gecko-mediaplayer soundconverter audacity oggconvert avidemux ffmpeg winff libdvdcss2 libdvdread4 libdvdnav4 vlc gxine libxine1-ffmpeg

You may need to do it a few  times if you get errors.

Note to self, don't ever jump to ru236's aid again.....

First of all, not being able to play a fricking DVD is NOT an emergency.  Secondly, on the MAIN PAGE of Ubuntu Forums, there is a section called MAIN SUPPORT CATEGORIES, one of which is called MULTIMEDIA AND VIDEO.  Click that and all of the information provided is on the stickies.  All you gotta do is look.  We are not your personal support staff.

---

### Post by NinjaNumberNine on 2009-10-02
[IMG]http://ubuntuforums.org/images/statusicon/thread_dot_hot.gif[/IMG] 	 	 		[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 	 	      		 		 			 				 					tags: hot keys, keyboard shortcuts, quick, urgent 					 					 					 					 					 					 				 			 			 			 			 			                         [COLOR=#4096EE]**[kubuntu]**[/COLOR] 			 			[Urgent: Is there a hot key for shutting down a program in Kubuntu?]("http://ubuntuforums.org/showthread.php?t=1230545") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1230545") [2]("http://ubuntuforums.org/showthread.php?t=1230545&page=2")) 		
  		  		 			 			 				NinjaNumberNine
:lolflag::lolflag::lolflag:

---

### Post by doas777 on 2009-10-02
> **NinjaNumberNine said:**
> [IMG]http://ubuntuforums.org/images/statusicon/thread_dot_hot.gif[/IMG]                   [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]                                                                                    tags: hot keys, keyboard shortcuts, quick, urgent                                                                                                                                                                                                                                         [COLOR=#4096ee]**[kubuntu]**[/COLOR]                          [Urgent: Is there a hot key for shutting down a program in Kubuntu?]("http://ubuntuforums.org/showthread.php?t=1230545")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1230545") [2]("http://ubuntuforums.org/showthread.php?t=1230545&page=2"))         
                                                               NinjaNumberNine
:lolflag::lolflag::lolflag:


so i hear that ninjas spend most of their time flying (when they are not cutting off heads), and that they are mammals. what are your thoughts on this?

realultimatepower.net


@op, follow the instructions I left in your other thread 40 minutes ago. if you do so, you will get to stop asking.

---

### Post by ru236 on 2009-10-02
geez im sorry if i offended everyone all im trying to do is get this resolved so i can move on i just thought this will be better than windows 
  once again sorry if every one got offended i wont do it again

---

### Post by doas777 on 2009-10-02
> **ru236 said:**
> geez im sorry if i offended everyone all im trying to do is get this resolved so i can move on i just thought this will be better than windows 
  once again sorry if every one got offended i wont do it again

not offended, really. just avoid making multiple threads on an issue (revise the one you have instead), and when people offer advice, take it. thats all.

---

### Post by ru236 on 2009-10-02
well ok and like i said i didnt mean to is just im new to linux and i was kinda freaking out  so thats why and it worked what you said to do thnks and i wont do it again so people calm down 
 everyone makes mistakes im sorry

---

### Post by NinjaNumberNine on 2009-10-02
That's fine, I guess I kinda started the criticism, sorry! Anyway back to the problem. What have you done so far?

EDIT: Have you read [this]("https://help.ubuntu.com/community/RestrictedFormats/")?

---

### Post by ru236 on 2009-10-02
ok, go here and follow the repository how to:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and install libdvd2css  per the instructions.

that shoudl do you. if not, open a terminal and run
 	Code:
 	sudo apt-get install ubuntu-restricted-extras 
after that, your DVDs shoudl play in most players (mplayer, totem, vlc, etc).

good luck


im folling this deal there right now

---

### Post by NinjaNumberNine on 2009-10-02
??? Why didn't you put that in your first post?:lolflag:

---

### Post by ru236 on 2009-10-02
like i said man im new to linux and most of this is kinda confusing

---

### Post by Paddy Landau on 2009-10-02
And you may find it useful to follow [this comprehensive multimedia & video how-to]("http://ubuntuforums.org/showthread.php?t=766683"), frequently updated.

---

### Post by Shibblet on 2009-10-02
> **ru236 said:**
> like i said man im new to linux and most of this is kinda confusing

And we dig that, man.  Keep in mind the best thing about Ubuntu, is the forums.  People are always willing to help, you don't need to say things like...

> HELP!!!!  My mother will die if I don't figure out how to run Compiz!

Although, that would inspire a quite a few look at clicks...

I think we might need a Read Before Posting Sticky: HOWTO: Asking questions in the forums.

Although, I'd prefer a Sticky: HOWTO: Start arguments in the forums.

---

### Post by ru236 on 2009-10-02
yea i understand but now whats happening is that it wiil play then suddendly my player just shuts off

---

### Post by HarrisonNapper on 2009-10-02
> **ru236 said:**
> yea i understand but now whats happening is that it wiil play then suddendly my player just shuts off

Just from experience, I would probably start a new thread for this issue, as it's separate. For the edification of other members of the ubuntu community, try running the program in a terminal and posting the output in the new thread on the original post. Anything you can do to provide extra information and go the extra mile will be appreciated by the community and I can guarantee you will appreciate the effectiveness of the responses they give.

On a side note, it takes a lot of brass to jump ship from Windows in to the unknown, so congrats and it's good to have you as a new member of the community.

---

### Post by Maheriano on 2009-10-02
okhereswhatyoudorunthemedibuntuthingytheninstallthelibstuffwhichitlookslikeyoudidandthentrythatdidyouputthedvdindiditworkmakesureyoudownloadvlcaswellfromthevlcwebsitekthxbai

That was about as easy to read as what you wrote.

---

### Post by HarrisonNapper on 2009-10-02
> **Maheriano said:**
> okhereswhatyoudorunthemedibuntuthingytheninstallthelibstuffwhichitlookslikeyoudidandthentrythatdidyouputthedvdindiditworkmakesureyoudownloadvlcaswellfromthevlcwebsitekthxbai

That was about as easy to read as what you wrote.

To which post are you referring?

---

### Post by ru236 on 2009-10-02
try putting a space between words

---

### Post by Maheriano on 2009-10-02
> **HarrisonNapper said:**
> To which post are you referring?

> **ru236 said:**
> try putting a space between words
In reference to the original post.

---

