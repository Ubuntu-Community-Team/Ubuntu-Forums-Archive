---
title: "Change resolution in nouveau on Lucid"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by fieseline on 2010-04-29
Hello,
after installing Lucid, I can't change screen resolution to higher than 1024x768 on a 19"-CRT. Is there any way to achieve a higher resolution? Creating an xorg.conf?
Thanks, fl

---

### Post by Cowboybebop79 on 2010-04-29
Have you enabled resricted drivers?

there should be an option for this in the system > administration > hardware drivers menu 

and what graphics card do you have that is more important than what size or spec your monitor is.

---

### Post by fieseline on 2010-04-29
Hello, you wrote:
> **Cowboybebop79 said:**
> Have you enabled resricted drivers?

there should be an option for this in the system > administration > hardware drivers menu 

and what graphics card do you have that is more important than what size or spec your monitor is.
sorry, this was not enough information. My card is Nvidia GeForce 5200, restricted drivers are not enabled. I activated it before, but I only came to a 600x xxx resolution. 
fl

---

### Post by Cowboybebop79 on 2010-04-29
Hey not everyone knows everything about computer hardware some people have a life :) . I have to say at the moment that I am not up to speed with nouveau invidia drivers as all my machines have ATI graphics at the moment. just want to check something first did you restart your computer after enabling the restriced drivers that come with the basic install? as they don't become active till after the restart.

---

### Post by fieseline on 2010-04-29
> **Cowboybebop79 said:**
> Hey not everyone knows everything about computer hardware some people have a life :) . 
Yes, that's true! I'm trying to get better in one of these;)
> **Cowboybebop79 said:**
>  just want to check something first did you restart your computer after enabling the restriced drivers that come with the basic install? as they don't become active till after the restart.
Yes, I did so (maybe I'm not as new as I'm supposed to be for this forum?). Restarting the computer ended in a nvidia-settings window that could not be used (buttons outside the screen :confused:) so I thought I'd give nouveau another try.

---

### Post by Cowboybebop79 on 2010-04-29
Hi sorry if I sound a bit patronising I don't intend to be its just sometimes there is a simple solution to a problem and is best to check all the basics first to rule them out before getting into the guts of something as it can turn into a big mess. Anyway I have tracked down a forum thread about changing the resolution in terminal with the xrandr command the basic command will give you a list of available resolutions and "man xrandr" without the quotation marks will give you the help file with all of the options of the xrandr command. Just mentioned this as a possible remedy to the initial resolution problem with the restricted invidia drivers.

---

