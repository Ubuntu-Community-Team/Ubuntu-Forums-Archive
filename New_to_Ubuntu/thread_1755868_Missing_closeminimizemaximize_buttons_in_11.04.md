---
title: "Missing close/minimize/maximize buttons in 11.04"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by egervari on 2011-05-11
This is a really frustrating problem and I was wondering if there was a more permanent fix out for this. 

For some reason, the close/minimize/maximize buttons are always disappearing on me. it's happening every few minutes now.

I have searched and found that ALT-F2 and typing 'compiz --replace' temporarily fixes it, but it just happens again and again.

This is starting to be a really big annoyance for me as it's interrupting my ability to get work done. I can't program more than a few tests without the entire title bar disappearing.

Is there anything I can do to fix this? I have done searches in google and on this forum, and it seems like this problem goes back to July of 2010...

Help?

---

### Post by rockstarrem on 2011-05-11
What Ubuntu version are you using? What graphics card do you have?

---

### Post by egervari on 2011-05-11
The title says I am using 11.04

My graphics card is an nvidia 9600 gt.

---

### Post by rockstarrem on 2011-05-11
I did a little searching and the only thing that I found helpful was this:

[http://ubuntuforums.org/showthread.php?t=1522143](http://ubuntuforums.org/showthread.php?t=1522143)
> **-humanaut- said:**
> hit alt+f2 and type gconf-editor
go to applications-->metacity--> and check the layout of the buttons make sure it looks like this menu:maximize,minimize,close (for right) or close,minimize,maximize:menu (for left)

Other than that, people say that keeping a terminal open with the command "metacity --replace" works until you close the terminal window. Maybe someone else could help out a little more, I've never experienced this myself.

---

### Post by egervari on 2011-05-11
I'll try the metacity one instead of compwiz. This sounds like what I am doing though.

Like wow... very annoying :(

---

### Post by wildmanne39 on 2011-05-11
> **egervari said:**
> This is a really frustrating problem and I was wondering if there was a more permanent fix out for this. 

For some reason, the close/minimize/maximize buttons are always disappearing on me. it's happening every few minutes now.

I have searched and found that ALT-F2 and typing 'compiz --replace' temporarily fixes it, but it just happens again and again.

This is starting to be a really big annoyance for me as it's interrupting my ability to get work done. I can't program more than a few tests without the entire title bar disappearing.

Is there anything I can do to fix this? I have done searches in google and on this forum, and it seems like this problem goes back to July of 2010...

Help?

Hi you might try resetting unity by typing unity --reset after you enter the command giveit a few minutes to run and do not worry about the errors the screen will display. When it is finished restart the computer. I hope this helps it fixed my problem that I caused by playing with compiz.:)

---

### Post by beew on 2011-05-11
If you switch to another desktop and then switch back the buttons will show up (no need to reset anything). This works in Unity. Not very elegant but the fastest way to do it before there is a permanent fix. 

I don't know if this problem happens in the classic desktop because I don't use it.

---

### Post by PunkLV on 2011-06-20
Bump.
Seems the issue still lies unresolved.

I've performed an upgrade yesterday to 2.6.39-2-amd64 kernel and upon reboot everything was working fine: cube, animations, everything$ except for the damn buttons. 

I've tried virtually all solutions found on the web to no avail. This makes me think that this is sololy a gnome-compiz issue which can only be fixed by the compiz devs.

Compiz output:
```

Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing place options...done
Initializing decoration options...done
Setting Update "initiate_button"
Setting Update "command"
Initializing put options...done
Initializing gnomecompat options...done
Initializing text options...done
Initializing crashhandler options...done
Initializing screenshot options...done
Initializing commands options...done
Initializing wobbly options...done
Initializing imgjpeg options...done
Initializing ring options...done
Initializing cube options...done
Initializing svg options...done
Initializing animation options...done
Initializing reflex options...done
Initializing workarounds options...done
Initializing shift options...done
Initializing animationaddon options...done
Initializing 3d options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing rotate options...done
Initializing cubeaddon options...done
Setting Update "put_pointer_key"
Setting Update "run_command_terminal_key"
Setting Update "directory"
Setting Update "command0"
Setting Update "run_command0_key"
Setting Update "run_command1_key"
Setting Update "darken_back"
Setting Update "title_font_bold"
Setting Update "title_back_color"
Setting Update "title_font_color"
Setting Update "next_slide_key"
Setting Update "color"
Setting Update "scale_image"
Setting Update "adjust_image"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "skydome_animated"
Setting Update "skydome_gradient_start_color"
Setting Update "skydome_gradient_end_color"
Setting Update "active_opacity"
Setting Update "minimize_effects"
Setting Update "focus_effects"
Setting Update "notification_daemon_fix"
Setting Update "qt_fix"
Setting Update "next_all_key"
Setting Update "min_cube_size"
Setting Update "width"
Setting Update "bevel"
Setting Update "initiate_all_button"
Setting Update "initiate_button"
Setting Update "rotate_left_button"
Setting Update "rotate_right_button"
Setting Update "rotate_left_window_button"
Setting Update "rotate_right_window_button"
Setting Update "reflection"
Setting Update "cylinder_manual_only"
Setting Update "draw_top"
Setting Update "draw_bottom"
Setting Update "top_scale"
Setting Update "bottom_scale"
Setting Update "top_aspect"
Setting Update "bottom_aspect"
Setting Update "top_clamp"
Setting Update "bottom_clamp"
Setting Update "top_color"
Setting Update "bottom_color"

```

GNOME3 version: GDM 2.30.5
Compiz version: compiz 0.8.4

I'm literally out of ideas and there is not much info floating around for me to understand what exactly is causing the issue.

Any help or guidance appriciated.

---

### Post by cfchase on 2011-07-06
I didn't see anything that really matched this on [launchpad]("https://bugs.launchpad.net/ubuntu") but I'm having the same problem.  If someone finds the bug, could they post the link?

I'd really like to get this fixed since it is incredibly annoying and hurting my productivity.  I'm a Ubuntu newb and would like to know what info would be helpful getting this fixed (compiz settings, etc) and where best to report it.

P.S.  I also have an Nvidia card, a 240M on 2 monitors.

---

### Post by CatKiller on 2011-07-06
> **egervari said:**
> I have searched and found that ALT-F2 and typing 'compiz --replace' temporarily fixes it, but it just happens again and again.

Restarting Compiz is overkill. ```
compiz-decorator --replace
``` is sufficient to get your window decorations back.

---

### Post by TinMan77 on 2011-09-13
I just had the same issue and cant get it fixed

---

### Post by Blasphemist on 2011-09-13
First, no offense to any of you. I always remember that you have to be sure all of the simplest solutions have been covered. 

I just want to be sure that there is no confusion here since where these buttons appear depends on whether or not the window is maximized or not maximized, and where your mouse is hovering for menus. Please look at this wiki page just to be sure. [https://help.ubuntu.com/11.04/ubuntu-help/shell-windows-states.html](https://help.ubuntu.com/11.04/ubuntu-help/shell-windows-states.html)

---

### Post by JD8182 on 2011-09-13
The way I fixed this issue is by going to System/Preferences/Compizconfig settings manager, at the bottom left corner above
 the close button is Preferences.Once inside the Preferences, under the Profile & Backend tab, under default profile (click reset to defaults).. Then reboot, hope this helps, good luck.

> **egervari said:**
> This is a really frustrating problem and I was wondering if there was a more permanent fix out for this. 

For some reason, the close/minimize/maximize buttons are always disappearing on me. it's happening every few minutes now.

I have searched and found that ALT-F2 and typing 'compiz --replace' temporarily fixes it, but it just happens again and again.

This is starting to be a really big annoyance for me as it's interrupting my ability to get work done. I can't program more than a few tests without the entire title bar disappearing.

Is there anything I can do to fix this? I have done searches in google and on this forum, and it seems like this problem goes back to July of 2010...

Help?

---

### Post by rollinsmoke on 2012-02-17
well i tried that last fix and lost my unity menu and all but hey thats fine with me id rather have just cairo dock and an old style start menu so far so good with me

---

### Post by PunkLV on 2012-02-17
This probably is a rather late reply.

However, I suggest you install gnome3, but if you are going to use compiz and gnome2 you quite possibly will have lots of patches and plugins to compile and install in order to get it all working, considering that Ubuntu had switched to Unity entirely. 

Anyway, I would advise you to check out other Linux distributions and intstall it without a DE, after that install whatever suits your needs on top of it. In case you have the time required and you really care.

---

### Post by vijay sajjan on 2012-04-03
thanks it worked for me

---

### Post by Ichido on 2012-07-26
> **vijay sajjan said:**
> thanks it worked for me

Which "Fix" worked for you?
Thanks.

---

