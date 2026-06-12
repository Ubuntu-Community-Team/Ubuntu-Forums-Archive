---
title: "gnome uses 95% CPU?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by tripzilch on 2011-02-15
(I'm running Ubuntu Netbook 10.04 on a Medion Akoya netbook)

Trying to make my system run more snappy, among other things I'm running Startup Application Preferences (gnome-session-properties) and I have "top" open in a gnome-terminal.

The gnome-session-properties is not the point here, because a lot of other applications show this behaviour as well, I just noticed it now cause I was keeping an eye on "top":

As I play a bit with the list of startup programs, I run the scrollwheel (trackpad area) up and down a couple of times. It's like the gnome-session-properties GUI goes into unstoppable bullet-time or something, the list goes up and down, taking its bloody time to perform every single movement I made with the scrollwheel, except it does it really at its own pace, making a few scrollwheel swipes easily last 20-30 seconds or so (and nothing I can do to cancel it).

In the mean time, I see what's happening in "top". The gnome-session-properties process is using 95% of my CPU.

It's moving a list with checkboxes up and down.

Can anyone explain me why it needs 95% of my 2GHz CPU to move a list of checkboxes up and down?

It's not like I'm asking it to fold proteins, build a rainbow table or perform global illumination raytracing or something.

What on earth could it be doing that it needs to calculate so much for? It's just CPU calculations, memory usage stays at a reasonable 1.3%.

Trying a few other applications I find that Transmission does the same thing, but not all applications do (Thunderbird is much slower, for instance, but on the other hand it never reaches more than 60% CPU).

I understand that this is probably a matter of the way Gnome handles all sorts of things like GUI updates and events (mousewheel scrolling).

But is there any way to configure this to be more efficient?

And if not, maybe I should try another window manager or theme (I have the default dark "Human" theme) or something and see if that works better?

Thanks for any advice.


(PS is this the right subforum? and if not, where should I have put it, I'd like to be able to do the right thing next time)

---

### Post by waynefoutz on 2011-02-15
Lxde (Lubuntu) is the fastest window manager in the Ubuntu family. Also, another idea, a youtube friend of mine made this tutorial on how to make a customized Gnome install using the minimal Ubuntu .iso file and a script that he wrote. The script and details are in the comments. I tried it out myself, it's pretty fast, and he cut the boot up time down substantially.

[http://www.youtube.com/watch?v=f0iGqChlHEw]("http://www.youtube.com/watch?v=f0iGqChlHEw")

---

### Post by rvchari on 2011-02-15
by running top, did you notice any runaway processes thats going on as a chain reaction ? this must be the culprit thats consuming ur cpu energy....
identify that. may be that should help ...

i am telling you i have a problem in my desktop appearance execution.
i have conky installed to trace the pid of processes. whenever i right click on desktop and go to change themes / appearance, cpu temperature and fan speed shoots up....
but when i kill with pid on terminal, it instantly reverts back to normalcy.
gnome appearance is the maximum i try to juggle around with tweaking and changing themes as frequently as i can !!!

---

### Post by mikewhatever on 2011-02-15
I guess all it does it redraw the window. What else did you expect?

> **rvchari said:**
> ...
gnome appearance is the maximum i try to juggle around with tweaking and changing themes as frequently as i can !!!

Is it like refreshing the desktop in Windows? I've read that Indians do that.

---

### Post by tripzilch on 2011-02-15
> **rvchari said:**
> by running top, did you notice any runaway processes thats going on as a chain reaction ? this must be the culprit thats consuming ur cpu energy....
identify that. may be that should help ...

I'm not sure what you mean here? Like, extra processes *appearing* when I abuse the scrollwheel? No I don't have any of those. Nor are there any other processes except for the one whose GUI I'm scrolling up and down.

And I don't have conky or other add-ons installed/running. The reason I'm asking this thread is because I just get the feeling Gnome is being rather sluggish overall. So as part of trying to fix that, I have disabled quite some things.

(Especially since I worked on my gf's laptop for a bit yesterday, which is older, has less CPU and RAM and is running Vista (not XP, not Win7, but *Vista*. AKA "Memory Hog") and it was like a breath of fresh air how responsive and speedy the GUI was.)

If I, instead of scrolling up and down real fast, would click buttons or switch tabs real quickly, it abuses the same amount of resources. Anything that stresses the GUI of a Gnome application. So I'm guessing the slowdown is either in handling the event or redrawing the window.

And before anybody says I should just use the GUI normally :) That's not really the point, the "stressing" is just a way to make the problem really apparent by magnifying the symptoms, when I use it normally it's also sluggish, but it's much harder to pinpoint the additional CPU usage.

For instance, this way I know that it's CPU, not memory. And I can also conclude that whatever is eating up the cycles, it's either the application itself or some thing that does not show in "top".

Anybody know that BTW? The window manager functions themselves, would they count as part of the CPU usage of the application they're used for? (Seems that's the case, since I've never seen them in a "top" listing, but if anyone knows for sure can confirm it, that's another possibility to strike off my list).

By the way, speaking of the "Appearances Preferences" window, if I "stress" the GUI there, it only reaches about 60-65% CPU, just like Thunderbird. So from that I can conclude there's at least two separate parts eating up the CPU cycles: One that eats about 60% CPU in *most* Gnome applications when stressed to the max, and another that eats an additional 30% in *some* Gnome applications (such as gnome-session-properties).

> I guess all it does it redraw the window. What else did you expect?

That's the thing, that would have been *exactly* what I'd have expected. Except it's obviously the case that redrawing the window is by no means "all it does", since 1) I can't imagine how that would require so much CPU power (but if it does, I'd like to know how and/or why, which was my question at the beginning of the thread) and 2) It doesn't happen with *every* application (for instance, Opera does not have this problem).

---

### Post by tripzilch on 2011-02-15
> **waynefoutz said:**
> Lxde (Lubuntu) is the fastest window manager in the Ubuntu family. Also, another idea, a youtube friend of mine made this tutorial on how to make a customized Gnome install using the minimal Ubuntu .iso file and a script that he wrote. The script and details are in the comments. I tried it out myself, it's pretty fast, and he cut the boot up time down substantially.

[http://www.youtube.com/watch?v=f0iGqChlHEw]("http://www.youtube.com/watch?v=f0iGqChlHEw")

Thanks for the tip, I'll check out the video, the comments and Lxde.

But I'd still like to know what Gnome is using all the CPU power for (as I find out more, I'll keep updating the thread).

---

### Post by Grenage on 2011-02-15
If I 'scroll like a madman' on firefox, one of my CPU cores hits 14% (Phenom II x4); I get the same in Nautilus.

I'd personally expect that - each scroll is a fresh render; have you ever used tried to scroll in FF on a really old machine with no GFX drivers installed?  What kind of GPU does the netbook have?  Is it a dedicated processor, or is it handled by the CPU?

---

### Post by rvchari on 2011-02-15
> **mikewhatever said:**
> I guess all it does it redraw the window. What else did you expect?



Is it like refreshing the desktop in Windows? I've read that Indians do that.

you r right... many do that (i am an exception !!! till date i keep wondering y they do this)
after reading your thread, i found one more thing on my setup...
whenever i go to appearance, there r 2 processes created, one pid is X and the next is X+1. it was the X+1 that created problems by keeping the cpu engaged and in the process increasing fan speed and ofcourse the temp.
when i kill the X+1 process, i am able to use the appearance window with ease (coz the original X pid) is live....
wonder whats making this to add up an X+1 pid...

when you correlate to your problem, there must be multiple pids created or atleast one additional pid.... check that out and perhaps your problem could be solved..

---

