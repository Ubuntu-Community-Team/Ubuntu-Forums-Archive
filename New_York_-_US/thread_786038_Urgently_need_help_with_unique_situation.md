---
title: "Urgently need help with unique situation"
date: 2008-05-07
forum: New York - US
---

### Post by crs501 on 2008-05-07
Background: I just recently upgraded from Ubuntu 7.10 to 8.04. I had originally tried to upgrade from the network via the Update Manager like all of us were invited to do. I thought it was going to go smoothly and then for no apparent reason --- and literally one minute away from being finished with the install --- the computer froze. I tried all I knew to do but eventually I had no option but to shut down my computer knowing full well the installation was incomplete and I was probably very screwed! I eventually managed to get online thru the GNOME option on my log-in screen, downloaded 8.04 and finally installed it successfully on 4/25/08. 
All was good, it worked very well and I was lovin' it until yesterday 5/06/08. I returned home from business and my wife told me about a problem she had while simply surfing and checking e-mail. She said the computer froze and she was unable to do anything. She shut the computer down, and when she turned it back on she discovered she was unable to boot back up. I don't know the full story as I wasn't here to see it all. What I saw when I tried to boot the computer was basically:

BUG: Soft Lockup-CPU#1 stuck for 11s! (hald-probe-vide:5775)

There were numbers preceding that line each time it appeared that looked like this:

[ 72.883132 ] and each time the line repeated the first two digit positions had progressively higher numbers than the previous. (does that make sense?)             .

I have tried numerous times to re-install Hardy Heron 8.04 with the install disc I burned, but with no luck --- The yellow bar on the black Ubuntu screen just gets so far and stops, not proceeding to the install process.

I have also downloaded Gutsy Gibbon 7.10. So my question is:
Under the circumstances, can I re-install 7.10 and then attempt the upgrade to 8.04 via the Update Manager without harming my computer?
Any advice would be helpful at this point, but I need it pretty quickly!!! We're simple users so answers have to be relatively simple as well. I'd appreciate any help here! Thanks.


PS: Those offering serious help can e-mail me at [email]crs501@hotmail.com[/email] ---- I do presently have limited ability to check e-mail. However I'm not certain that I'll be able to get any online ability back tomorrow if I turn this thing off tonight. ya dig? I'll keep checking the "Pidgin" just in case.

---

### Post by agim on 2008-05-07
This might be a hardware issue. Sounds like you are having cpu issues.

---

### Post by crs501 on 2008-05-07
Thanks for the response "agim"!  i took a look at my System Monitor and CPU#1 seems to be running generally between 78-86%, and CPU#2 between 12-22% --- which I believe are where they normally are. Anyways, I ran a Hardware Test and sent it out to Launchpad.  I believe they will report back to me if anything is off, correct?

I've posted this in several forums, and I'm still wondering about whether I can safely backtrack to 7.10 and then upgrade to 8.04 or not. Hopefully somebody knows the answer!  Thanks again!!!

---

### Post by twright on 2008-05-07
you can install 7.10 and upgrade, but if you are having hardware issues that might not help

---

### Post by crs501 on 2008-05-07
Thank you "twright" for the response. So my cockeyed idea to backtrack and then attempt the upgrade will work, huh?!?  I was hoping so, but didn't want to do any permanent damage of any sort as I can't afford to buy a new computer if I should muck it up somehow. And I'm running Ubuntu (since a Windows XP failure last Fall) because I can't afford a new Windows OS, and since I've been on Ubuntu I really like it!  Anyways, I've downloaded and burned installation disks for both 7.10 and 8.04, I'll continue to see what responses I get tonight and I'll begin trying everything I can tomorrow. Thanks again twright!!!

---

### Post by AndrewTheArt on 2008-05-07
You can "safely" backtrack. The only thing you really need is the contents of your /home partition or folder (whatever user's data you want to save). If you burn this folder on a DVD or find some way to install 7.10 without messing with the /home partition/folder, you should be perfectly OK.

---

### Post by crs501 on 2008-05-09
I have successfully "Down-graded" to Gutsy Gibbon 7.10. I have tried upgrading to Hardy Heron 8.04 numerous times and have nothing but problems. At least one responder to my posts on these forums suggested I might have a CPU or Hardware problem. Yet, each time I went back to Gutsy 7.10 everything works fine and I cease having the problems I encountered on 8.04. Seems to me if there were hardware issues, they would appear no matter what I was running. PLUS: a lengthy scan of posts all over these forums reveal numerous people experiencing major issues with both 8.04 and the new Firefox similar to mine. I'm feeling lucky to have safely returned to a smooth-running Gutsy 7.10, and since I realize support for Gutsy is inevitably limited, I am contemplating scraping together the money to return to good old vulnerable XP SP2. After the past 6-7 months I've enjoyed the differences Ubuntu has to offer, but the problems I've dealt with make battling viruses and spyware on XP look like a walk in the park on a sunny day! Sorry guys, gotta be honest!!!

---

### Post by Amanda HazLaPaz on 2008-05-31
Waiting just another few months might be a solution to your issue. The developers will continue working on Hardy to make fixes, and the updates will be farmed out to Ubuntuers. 

Using Gutsy for another three to six months won't mean you will lose all of your data and you'll never be able to print, edit, create, or process again. 

Think about it like a baby: sometimes babies look like they're ready to start walking, they take a few steps and fall down, then they spend a long while back on their knees. All it is is a re-configuring going on in the brain while the brain says "Okay, let's get some more practice here, build some pathways there, sleep and eat some, watch other people walk and  integrate all that into another try."

I truly hope you will consider using Gutsy for a few months longer. Early adopters of anything are usually the ones who have to 'suffer' while stuff gets figured out.

---

### Post by twright on 2008-06-01
> **crs501 said:**
> I have successfully "Down-graded" to Gutsy Gibbon 7.10. I have tried upgrading to Hardy Heron 8.04 numerous times and have nothing but problems. At least one responder to my posts on these forums suggested I might have a CPU or Hardware problem. Yet, each time I went back to Gutsy 7.10 everything works fine and I cease having the problems I encountered on 8.04. Seems to me if there were hardware issues, they would appear no matter what I was running. PLUS: a lengthy scan of posts all over these forums reveal numerous people experiencing major issues with both 8.04 and the new Firefox similar to mine. I'm feeling lucky to have safely returned to a smooth-running Gutsy 7.10, and since I realize support for Gutsy is inevitably limited, I am contemplating scraping together the money to return to good old vulnerable XP SP2. After the past 6-7 months I've enjoyed the differences Ubuntu has to offer, but the problems I've dealt with make battling viruses and spyware on XP look like a walk in the park on a sunny day! Sorry guys, gotta be honest!!!
you can always use hardy with gutsy's kernel (the core system) so you get all the new programs

a new version of ubuntu will be out before gutsy goes out of support

---

