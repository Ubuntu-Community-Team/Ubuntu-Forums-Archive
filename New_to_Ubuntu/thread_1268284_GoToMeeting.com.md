---
title: "GoToMeeting.com"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by AlistairH on 2009-09-16
Does anyone have any experience of this company's services under Ubuntu?

I've been invited to attend a number of online webinars hosted on GoToMeeting's servers. All I get is a page telling me I'm using an unsupported operating system.

Is there a way of fooling them into thinking I'm running windows, by changing the OS as reported by Firefox for example.

If no no matter, I will do without as I'm not going to kowtow to a firm supplying Internet services who excludes users who refuse to follow the herd.

That said, if anyone knows of cross-platform, free to use conferencing services, let me know. I could pass that on to my contacts and suggest they switch.

Thanks in advance.

---

### Post by zeroseven0183 on 2009-09-16
Did you try using Internet Explorer through Wine?

If not, may be you can consider that. Follow the instructions here: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by sandyd on 2009-09-16
if their not using activex or something native to ie, then
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
will sufface.

---

### Post by AlistairH on 2009-09-17
ZeroSeven: I'm trying to avoid IE out of principle. If I cannot get in natively via firefox/linux then I won't go at all.

Carlee: There's another meeting scheduled tonight so I'll give that addon a go.

Thanks for the advice folks.

---

### Post by AlistairH on 2009-09-17
No luck with the Firefox addon Carlee. It allowed me to get in and register, which is further than I normally get, but when I tried to connect to the meeting, it wants me to download and install a windows .exe file.

Not having that so I'll have to go without.

Thanks anyway.

---

### Post by shae on 2009-09-17
GoToMeeting uses a program installed on your computer, but I believe it is Windows only.

Like you, I want to know if there is some sort of Linux alternative to this?

---

### Post by SunnyRabbiera on 2009-09-17
> **shae said:**
> GoToMeeting uses a program installed on your computer, but I believe it is Windows only.

Like you, I want to know if there is some sort of Linux alternative to this?

[http://www.dimdim.com/](http://www.dimdim.com/)
Might help...
The cost we pay for a MS only world

---

### Post by steveneddy on 2009-09-17
Either run Windows in a virtual machine like VirtualBox or go to a   different service:

[http://www.megameeting.com/](http://www.megameeting.com/)

[http://www.flyteblog.com/flyte/2007/06/yugma-free-web-.html](http://www.flyteblog.com/flyte/2007/06/yugma-free-web-.html)

[http://useopensource.blogspot.com/2007/08/open-source-web-conferencing.html](http://useopensource.blogspot.com/2007/08/open-source-web-conferencing.html)

and finally:

[http://www.ganconference.com/](http://www.ganconference.com/)

I used to have to do GoToMeetings and just kept a windows machine around for that purpose.

I haven't tried GoToMeeting in a VM but would be interested to know if it works.

EDIT:

These results were all from a Google search for **Linux Web Conferencing**

---

### Post by LewRockwell on 2009-09-17
> **AlistairH said:**
> No luck with the Firefox addon Carlee. It allowed me to get in and register, which is further than I normally get, but when I tried to connect to the meeting, it wants me to download and install a windows .exe file.

Not having that so I'll have to go without.

Thanks anyway.

whatever they're selling...

especially in windows-stuff-only-wonderland...

you'll probably be better off without...anyways...

.

---

### Post by AlistairH on 2009-09-18
I've suggested to my contacts who host these webinars that they take a look at yugma.com. If that goes OK, I'll be able to attend their sessions.

Failing that, I'll have to decline my invitations as I don't want to go the windows route, either with a spare machine or in wine, out of principle.

Thanks for the feedback folks.

---

### Post by kiwiboyus on 2009-09-21
Hi there,

I actually work for Citrix Online (GoToMeeting, GoToMyPC GoToAssist), and we are looking into adding support for Linux. Currently our software runs on Windows and Mac, GoTomeeting will run in a VM but not in Wine. If you are unable to attend a meeting try asking the Organizer to use the built in recording feature and making the WMV available to you. 

There are a number of Linux users here (myself included), and we are actively campaigning for Linux support.

Thanks,

---

### Post by AlistairH on 2009-09-23
Thanks for the info kiwiboyus.

We have used the recording feature in GoToMeeting in the past. It's in the nature of the meeting subject matter that makes watching a recording of limited value.

Good to see that you're looking to support Linux. Any idea when that may materialise?

---

### Post by spottedhog on 2009-09-25
I second that emotion about Linux Support for the GoToMeeting set of applications.  But if Citrix is not wanting to support Linux, then they have lost a customer or 3.

---

### Post by rburkartjo on 2009-09-25
if i remember correctly(from their add on tv) gotomeeting will only work with windows or mac linux is not supported

---

### Post by LarryJ2 on 2009-11-09
My wife signed up for an on-line class that is taught using GoToMeeting.  She's all M$ windows and I'm all linux.   On her PC we couldn't get the microphone working so I signed up for a temporary trial account and set up a meeting for us to experiment with.  To do that,  I installed XP under VirtualBox 3.0 then installed GoToMeeing coordinator trial version.  So GoToMeeting host program (coordinator version?)  ( anyway, the person that schedules meetings and emails the link to them)  runs fine in Ubuntu Karmic 9.10 in a VirtualBox vm running an ancient copy of XP. My guess is that the GoToMeeting client (participant) version would run in a virtualized XP environment also.

The latest hitch is that the class lecturer offered up a recording of one of their on line sessions.  My wife downloaded the huge file but when she tried to open it,  she got a message complaining about the lack of a codec. Only the audio, not the video would play. After fussing around,  we found the codec availabe for downloading into your M$ window machine or into your M$ windows vm here:  

[https://www2.gotomeeting.com/codec?Portal=www.gotomeeting.com](https://www2.gotomeeting.com/codec?Portal=www.gotomeeting.com)


Apparently the format for the GoToMeeting recordings is .wmv wrapped in some obscure M$ encryption scheme.  Would be nice of the meeting video arrived in a .mp4 format!  The codec apparently deals with the G2M3  video/a-xsf format.  If you try to view the recording in linux,  the player complains about the lack of a G2M3 codec. For example, VLC reports **" no suitable decoder module for fourcc `G2M3'. VLC probably does not support this sound or video format"**  The audio plays OK but no video.

---

### Post by kiwiboyus on 2009-11-09
> **LarryJ2 said:**
> My wife signed up for an on-line class that is taught using GoToMeeting.  She's all M$ windows and I'm all linux.   On her PC we couldn't get the microphone working so I signed up for a temporary trial account and set up a meeting for us to experiment with.  To do that,  I installed XP under VirtualBox 3.0 then installed GoToMeeing coordinator trial version.  So GoToMeeting host program (coordinator version?)  ( anyway, the person that schedules meetings and emails the link to them)  runs fine in Ubuntu Karmic 9.10 in a VirtualBox vm running an ancient copy of XP. My guess is that the GoToMeeting client (participant) version would run in a virtualized XP environment also.

The latest hitch is that the class lecturer offered up a recording of one of their on line sessions.  My wife downloaded the huge file but when she tried to open it,  she got a message complaining about the lack of a codec. Only the audio, not the video would play. After fussing around,  we found the codec availabe for downloading into your M$ window machine or into your M$ windows vm here:  

[https://www2.gotomeeting.com/codec?Portal=www.gotomeeting.com](https://www2.gotomeeting.com/codec?Portal=www.gotomeeting.com)


Apparently the format for the GoToMeeting recordings is .wmv wrapped in some obscure M$ encryption scheme.  Would be nice of the meeting video arrived in a .mp4 format!  The codec apparently deals with the G2M3  video/a-xsf format.  If you try to view the recording in linux,  the player complains about the lack of a G2M3 codec. For example, VLC reports **" no suitable decoder module for fourcc `G2M3'. VLC probably does not support this sound or video format"**  The audio plays OK but no video.

Hi there,

GoToMeeting recordings are compressed with a codec however the Presenter of the meeting can change their recording preferences so that a normal uncompressed WMV file is created instead. As I mentioned in my previous post here we are looking to add support for Linux, we are also taking another look at how we do recording.

Thanks,

---

### Post by beow on 2010-03-29
> **kiwiboyus said:**
> Hi there,
As I mentioned in my previous post here we are looking to add support for Linux

Great! After much hazzle with setting this up in Virtualbox this morning I really support this and wish you good luck with your efforts. Please keep us informed.

---

### Post by spril4 on 2010-07-14
> **kiwiboyus said:**
> Hi there,

I actually work for Citrix Online (GoToMeeting, GoToMyPC GoToAssist), and we are looking into adding support for Linux. Currently our software runs on Windows and Mac, GoTomeeting will run in a VM but not in Wine. If you are unable to attend a meeting try asking the Organizer to use the built in recording feature and making the WMV available to you. 

There are a number of Linux users here (myself included), and we are actively campaigning for Linux support.

Thanks,

Thanks for posting that you're trying to support a standard video format--it gives me some hope!  I want to add though that I disagree with your statement that "our software runs on Windows and Mac".  The G2M3 codec may *run* on both, but it doesn't actually *work* on any of our 2 Windows or Mac computers!!

I've never seen a codec so badly designed that the audio and video play at different rates, but that's what happens on Windows.  The audio goes at full speed, and the video plods along much slower--making the combined result useless and unwatchable.  I have no idea how the programmers screwed up that one, but it's very unprofessional.

On my Mac, the video displays in very low resolution, and the audio doesn't work at all.

I can't imagine what committee of Citrix managers decided that, given  the dozens of well-written, proven video formats that have been working  for years, they needed to create their very own hideously slow format  that requires installation of custom software and doesn't work even  then.

G2M3 is a CPU-hogging dog that should be shot immediately to put us out of its misery!

-Tom

---

### Post by kiwiboyus on 2010-07-14
Hi Tom,

When recording with GoToMeeting you can set the Preferences to automatically remove the codec once the recording is finished, this gives you a plain WMV file that you can edit, convert or share. If you plan to share the recording with a Mac user you will need to convert the recording as noted in our FAQs [http://www.gotomeeting.com/fec/online_meeting_support](http://www.gotomeeting.com/fec/online_meeting_support) 
I'm not sure why you had issues on Windows, it's definitely not the norm and I suggest you call our toll free support for assistance [http://support.gotomeeting.com](http://support.gotomeeting.com)

Thanks,

---

### Post by spril4 on 2010-07-14
Thanks for your message!  Since we're only attending this presentation,  we don't have the ability to set the recording preferences.  But we did  collaborate with the presenter to finally find a workaround for  GoToMeeting's shortcomings.

After hours of frustration, support emails, codec downloads and media  player re-installations, we finally got the GoToMeeting G2M3 format to  work by using *two* computers simultaneously. The Windows machine could play the audio (but not the video).  The Mac couldn't played the audio, but could play the video in a very choppy low-res display.  So we moved the Mac notebook to the Windows desktop, started both with a countdown--and sent our calls straight to voicemail.  We had to keep pausing audio so the video could catch up since they still weren't synchronized (Of course, we knew better than to even try on Linux.)

We have to laugh that this is Citrix in the 21st century!

-Tom

---

### Post by kiwiboyus on 2010-07-14
Hi Tom,

As I said your experience on the Windows PC was definitely not normal. For anyone else in a similar situation where they are given a recording in the GoToMeeting format here are 2 easy guide to removing the codec after the fact:

[Edit and re-encode your recording with this single free application.]("http://glenndcitrix.wordpress.com/2010/06/04/edit-and-re-encode-your-recording-with-this-single-free-application/") 
[How to convert a GoToMeeting, GoToWebinar or GoToTraining formated recording to something else.]("http://glenndcitrix.wordpress.com/2010/04/06/convert-recordings/")

We introduced the recording feature a number of years agao now, before we even offered support for Mac, this is why the codec is PC only. As I mentioned above, we are over hauling the recording feature this year which will not only make it Mac compatible but also much easier to share your recordings.

Thanks,

---

### Post by mynis01 on 2010-10-05
Thank you for taking the time to reply to this thread kiwiboyus. I have to use gotomeeting for a class I'm in and it's very irritating that I have to not only use windows to use it but also install some type of active-x control. I hope that Linux becomes supported soon because it appears that this software is very commonly used and I will be taking online classes for probably the next five years.                     :neutral:

---

### Post by cyrano24100 on 2010-12-03
Hear, hear, yes, I too SO WISH that GoToMeeting could support Ubuntu/gnome ... We are starting to use Ubuntu machines more and more in my company, and we NEED gotomeeting so we always end up using old washed-up windows XP boxes for any of our teleconferences...

---

### Post by jnguyen on 2011-02-16
> **steveneddy said:**
> Either run Windows in a virtual machine like VirtualBox or go to a   different service:

[http://www.megameeting.com/](http://www.megameeting.com/)

[http://www.flyteblog.com/flyte/2007/06/yugma-free-web-.html](http://www.flyteblog.com/flyte/2007/06/yugma-free-web-.html)

[http://useopensource.blogspot.com/2007/08/open-source-web-conferencing.html](http://useopensource.blogspot.com/2007/08/open-source-web-conferencing.html)

and finally:

[http://www.ganconference.com/](http://www.ganconference.com/)

I used to have to do GoToMeetings and just kept a windows machine around for that purpose.

I haven't tried GoToMeeting in a VM but would be interested to know if it works.

EDIT:

These results were all from a Google search for **Linux Web Conferencing**

------------------------------------------------------------------------------------------------------

It works very good. I have a D830 laptop & T3400 workstation both from Dell at work running GNOMEUbuntu 10.10 with VMWare player (free) installed to use Windows XP because I need older IE and GoToMeeting for tech support.

jvn

---

### Post by Old *ix Geek on 2011-02-16
I feel *VERY* strongly that the solution to issues like this does not include jumping through hoops and forcing yourself to use windoze/IE, but instead involves contacting the company and telling them they're excluding you and others because of their ignorance.

Every time a Linux user resorts to using windoze and/or IE to access an ignorant site, that site's stats continue to show that only windoze/IE users are accessing it. Instead, each Linux user needs to access the site with their usual OS/browser, find the 'contact us' link, and drop them a note saying you'd love to use their service, buy their products, whatever, but you're unable to because they're trying to dictate what software you use.

Does anyone remember when there was a plethora of "IE only" web sites? Do you have any idea why those went the way of the dinosaurs? Because of people like me who religiously contacted sites and said "you're excluding me because I use Linux as my OS and SeaMonkey as my browser--and you really need to stop assuming that everyone is a windoze user." It worked. :D

So get off your butts and start VOICING your feelings to the companies involved instead of figuring out ways to use windoze to access their sites.

EDIT: I just want to point out something else--GoToMeeting.com runs on Linux and Apache. Doesn't it strike anyone else as odd that a company that relies on Linux for its very survival ignores its customers who use Linux? SPEAK UP. Tell them you--just like them!--use Linux and you want them to support your use of their site.

---

### Post by pedrogk on 2011-03-03
*Sigh*

Anybody knows if there is at least some kind of experimental way of attending GoToMeeting sessions from linux? (other than a windows virtual machine).

I will host an online conference for software developers on GoToMeeting, and about 15% of the audience are linux users. Some of them won't mind booting into windows or using a vm, but others would rather try to make it work in linux, even through experimental methods.

---

### Post by teejay17 on 2011-04-05
> **kiwiboyus said:**
> Hi there,

I actually work for Citrix Online (GoToMeeting, GoToMyPC GoToAssist), and we are looking into adding support for Linux. Currently our software runs on Windows and Mac, GoTomeeting will run in a VM but not in Wine. If you are unable to attend a meeting try asking the Organizer to use the built in recording feature and making the WMV available to you. 

There are a number of Linux users here (myself included), and we are actively campaigning for Linux support.

Thanks,
How's the campaign coming along? It would be fantastic if GoToMeeting supported the Linux platform.

---

### Post by spikoley on 2011-04-12
I love GoToMeeting.  It would be great to see a Linux version.

---

### Post by Gremlyn1 on 2011-05-02
Well I attempted to get GoToMeeting set up in my WinXP guest today and everything works fine until I try to get my microphone to work. Audio is good, but if I dare try to access the audio preferences menu and alter the hardware device for the microphone, the program freezes so horrendously that I can't even kill the program from the task manager and/or restart the computer without hitting the manual restart :(

I absolutely require g2m for work, unfortunately, and can't fathom having to setup my laptop to dual boot! Anyone have any ideas?

---

### Post by btolman on 2012-02-17
Not a beginner, but I thought I would bump this and see if there is any progress.

I saw a citrix booth at SCaLE10x and quite a lot of people were asking about support for both hosting and clients.

---

### Post by Scott Baker on 2012-02-17
I have to agree with some of the other posters here. The only way we're going to get results from these third party vendors, is to become a pain in their butts. Go to their sites, and let them know "we're here, and we'd like to have access to your line of products"!! Case in point "Skype". It's available for us because there is interest in the product ( and let's face it, it works with few, if any issues ). :-({|=

---

### Post by HDave on 2012-04-06
> **Scott Baker said:**
> I have to agree with some of the other posters here. The only way we're going to get results from these third party vendors, is to become a pain in their butts. Go to their sites, and let them know "we're here, and we'd like to have access to your line of products"!! Case in point "Skype". It's available for us because there is interest in the product ( and let's face it, it works with few, if any issues ). :-({|=

This is 100% correct.  For gotomeeting.com go here and fill out the form...politely asking about Ubuntu support.  It takes about 30 seconds.

[http://www.citrixonline.com/collaboration/product_support](http://www.citrixonline.com/collaboration/product_support)

---

