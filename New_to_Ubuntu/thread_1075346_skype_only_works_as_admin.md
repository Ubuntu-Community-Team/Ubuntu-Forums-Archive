---
title: "skype only works as admin"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Linux&amp;Gsus on 2009-02-20
Hi all.
Got a bit problem here with Skype. Since others don't want to switch to something else (e.g. Jabber) and I don't know of an alternative that is pretty much equally featured like Skype, I finally need to get this fixed, I guess.

So, my problem is that I can't start up Skype unless I execute it from command line with "sudo skype".
I don't think this is normal and should be like that, at least on other machines it works as ordinary user. That's why I hardly used it in a while.
But I have no clue what the solution to this might be. Is there somebody who can help me out with this?
I have Kubuntu 8.10 w/ KDE4.1. In case it matters.

Cheers.

---

### Post by cakuzo on 2009-02-20
How did you install Skype? Manually, per synaptic, per apt? With which version of skype do you face this problem?

---

### Post by arochester on 2009-02-20
How did you install it? If you have added the Medibuntu Repository then it appears as a package which can be installed by Package Manager.

---

### Post by Linux&amp;Gsus on 2009-02-20
Thanks for the reply.
I must confess that I can't remember exactly how I installed it. Sorry, I was a bit short on detail in my post up there.

I had it installed and running just fine before 8.10 and after upgrading to Ibex Skype wasn't working properly anymore (yes it's that long and that much that I cared about it sofar... :( ). I do remember that I had trouble installing it, though. I couldn't find it anywhere in the repos and finally downloaded it from the Skype website.
Installed version is 2.0.0.72.

Thanks for the help.
Cheers.

---

### Post by Bölvaður on 2009-02-20
It is in the medibuntu repos (google it to get instructions how to access that repos).
Before installing it from there you need to purge (completely uninstall) skype.

---

### Post by Linux&amp;Gsus on 2009-02-20
So, you think a re-install will fix it?
Will try that.

Ahhh, is a bit embarrassing, but how do I uninstall when not installed through the repos? Is it the same command?

Cheers.

---

### Post by superprash2003 on 2009-02-20
yes.. sudo apt-get remove skype

---

### Post by Linux&amp;Gsus on 2009-02-20
OK, here is what I did:
- Uninstall Skype (with purge)
- Check the repos, I couldn't find skype although I could find VLC. Shouldn't they both be in the Medibuntu repo? Anyways...
- Add Medibuntu repo and GPG key and update the source list
- Install Skype via apt-get (could find it now with a search)
- Installation finished without any error
- I can start Skype as ordinary user but not sign in. Message is displayed "Another Skype instance may exist" (See attached screenshot)
- Starting from terminal doesn't make a difference and no errors are displayed.
- After quiting Skype and trying "ps -ef | grep skype" no skype process is running, except the grep, of course.
- Starting and signing in from terminal with "sudo skype" works semi fine. Get the following output in the terminal:
```
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
```
But that shouldn't be the problem for the ordinary user, right?

Any ideas?

---

### Post by alexandari on 2009-02-20
maybe a dumb idea but, alt+f2 and killall skype?

---

### Post by Linux&amp;Gsus on 2009-02-20
don't know what alt+f2 should do, nothing happens (ubuntu vs kde??) but i tried in a terminal, output:
skype: no process killed

Edit: It's 3:40AM going to sleep now and work on suggestions tomorrow, well, later.
Thanks for all help so far.
Cheers.

---

### Post by Bölvaður on 2009-02-21
I would assume this is very rare problem, never seen anyone complain about the same thing here on the forums and I have never had anything to complain about when I have installed skype.


Perhaps changing from puse to alsa or the other way round might help solve the errors.

You may want to purge again and manually hunt down all remaining files to be 100% sure there have been any leftovers....... this will probably not help and you probably will not find anything either... but it's something.

---

### Post by Linux&amp;Gsus on 2009-02-21
> **Bölvaður said:**
> I would assume this is very rare problem, never seen anyone complain about the same thing here on the forums and I have never had anything to complain about when I have installed skype.
Makes me feel special. Kind of... :D
Although, I'm not sure if I feel proud about it.


> **Bölvaður said:**
> Perhaps changing from puse to alsa or the other way round might help solve the errors.
I'm not so worried about these errors, to be quite honest. Unless someone tells me that this is the solution to my problem. I put that in for the sake of completeness. You never know, really... But I might get onto this, anyways, when I don't see any other chance of success.



> **Bölvaður said:**
> You may want to purge again and manually hunt down all remaining files to be 100% sure there have been any leftovers....... this will probably not help and you probably will not find anything either... but it's something.
Well, I might have to do that. But I must say that I hate to search through every folder and check if there is something that has to do with Skype.
But what else can I do really... :(

Cheers.

---

### Post by kingbilly on 2009-03-02
Perhaps it is not that rare..

I have the same problem as well.  
ubuntu 8.10

> ALSA lib ../../../src/pcm/pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi

I had the bluetooth error in the terminal as well, but I fixed that by removing bluetooth packages from my computer, which doesn't have any bluetooth whatsoever

---

### Post by Vantrax on 2009-03-02
Did you install skype through apt, or as a source package or something similar?

Ive seen a similar problem before and it was cause because he didn't install skype via apt, and as such couldn't remove it via apt. He had to manually remove the files, then do an apt install.

---

### Post by pspsampsp on 2009-03-03
i would suggest you remove skype a gain and install it using the official skype repo which is:deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free   
also that another instance is running thing obviuosly means another skype is running just shutdown your pc and turn it on again and skype should work

---

### Post by Linux&amp;Gsus on 2009-03-06
I have Skype installed via apt, from the medibuntu repo I believe it is. I removed and installed it several times. Nothing seems to really fully help.
I might check out the bluetooth as kingbilly suggested. However this, while it's a bit getting on my nerves, isn't the actual big issue since Skype still works. Sound, video, chat, all is functioning properly. It just pops out the error messages all the time.

My real concern, though, is that I can start Skype only via terminal with sudo. So, basically Skype is running with administrator privileges all the time.

Also, I had originally a Skype repo in the list but that seemed to stop working and I have failed to find a official Skype repo ever since. But that might be just me...
I have the impression, though, that Skypes little interest in the Linux even dropped further down the pipe. There is a version 4.0 out for Windows but the latest Linux version must be over a year old by now.
Same goes for Gizmo5, Linux development is rather slow and the latest version is outdated.

I found TokBox, a free conference video chat system. Still seems like a rather new player on the field but they have trouble with supporting Linux on their (flash based) website. But at least the client development seems on par. Which actually requires Adobe AIR to run.

So, since most folks are on Skype I would like to get that working properly. Gizmo5 seems to be even worse than Skype, to me anyways, and TokBox would need some more attention for the Linux users but imho has the potential to become the next big thing for video chats.
But at this point I have no clue how to remove Skype (properly??) and install it so that it works as it should. Means as ordinary user. However, it seems to me that I should stick to it at least for the next time until some other VoIP / video chat option comes up.

Cheers.

---

