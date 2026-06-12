---
title: "Conky not starting up"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by UpSignal on 2010-04-09
Hi guys, i installed conky yesterday, and i've been playing around, however i can't set it to starup with ubuntu. I searched a lot on google, and tried all the solutions. Kinda frustrated. here's what i've done so far:

1 -  my conky file:
> #avoid flicker
double_buffer yes

#own window to run simultanious 2 or more conkys
own_window  yes
own_window_transparent yes
own_window_type override
own_window_hints undecorate,sticky,skip_taskbar,skip_pager 

# Fork to background
background yes

#borders
draw_borders no
border_inner_margin 3

#shades
draw_shades no

#position
gap_x 0
gap_y 34
alignment bottom_middle

#behaviour
update_interval 1

#colour
default_color  606060
#default_shade_color 000000
own_window_colour 333333

#font
use_xft yes
xftfont sans:size=10

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

#to prevent window from moving
use_spacer none
minimum_size 1920 0
maximum_width 1920

#mpd
#mpd_host localhost
#mpd_port 6600

TEXT
${alignc}  Kernel $kernel $machine ~ Updates ${execi 3600 aptitude search '~U' | wc -l | sed 's/^0$/none/'} :: RAM $mem/$memmax :: CPU $cpu% :: Home ${fs_used /home}/${fs_size /home} :: IP address: ${addr wlan0}  $alignr${time %d %b}  $alignr${time %H:%M    }

The file is named "conky.rc" and it's placed on my home folder "

This file is working, no problems. Now, for startup i have created another file called: "conky_start.sh" i used the command for making it executable, and then added to my startup applications. here's the file:

> #!/bin/bash
sleep 5 &&
exec conky -c /home/upsignal/conky.rc &
exit

the command on startup is: /home/upsignal/conky_start.sh

Now, the weird thing is.... when the computer starts, nothing happens, but...if i open alt+F2 and run "conky -c /home/upsignal/conky.rc" , it opens with no problem! it's very weird.
any ideas? thanks in advance

Using ubuntu karmic koala, and conky last version

---

### Post by TeoBigusGeekus on 2010-04-09
What if you tried 
```
#!/bin/bash
sleep 5&&
conky
```
for a start up script?

---

### Post by UpSignal on 2010-04-09
doing alt+F2 and running "conky" will open the uggly default script, not mine. unless is there anyway to force conky opening mine by default :s

---

### Post by TeoBigusGeekus on 2010-04-09
Rename or delete the default script and omit the exit command from your script.

---

### Post by UpSignal on 2010-04-09
Ok, here's what i just did:
made my script default. now it runs by typing "conky" , so i made your code:

#!/bin/bash
sleep 5&&
conky

made the file executable with
chmod a+x .conky_start.sh

and added to startup.
unless the "5" means 5 hours...it's not working :s

---

### Post by TeoBigusGeekus on 2010-04-09
What if you increase the sleep time, ie sleep 10?
EDIT:
Make the command for the script 
```
[COLOR="Red"]sh[/COLOR] /home/upsignal/conky_start.sh
```

---

### Post by UpSignal on 2010-04-09
Just before you post that, i tried with 10. it worked like a sharm. thank you so much for your time and script correction. Maybe it's incompatible with some other stuff in the boot and can't run right on 5 secs. anyway, thanks again

---

