---
title: "Conky Errors"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-19
Hi All,

I am having a few Conky errors.

Firslty here is my conkyrc file:

```

    background yes
    use_xft yes
    xftfont Arial:size=10
    xftalpha 0.1
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color Green
    alignment top_right
    gap_x 12
    gap_y 12
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256
    no_buffers yes

    TEXT
${font Arial:bold:size=12}${color Tan1}WORLD TIME ${color DarkSlateGray} ${hr 2}
$font${color Green}Boston$alignr${tztime America/New_York %T}
$font${color Green}London$alignr${tztime Europe/London %T}
$font${color Green}Kolkata$alignr${tztime Asia/Kolkata %T}
$font${color Green}Singapore$alignr${tztime Asia/Singapore %T}

${font Arial:bold:size=12}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color Green}Uptime ${color Red}$alignr${uptime}
   
$font${color Green}CPU1  ${color Red}${cpu cpu1}%  ${color Green}${cpubar cpu1} 
$font${color Green}CPU2  ${color Red}${cpu cpu2}%  ${color Green}${cpubar cpu2} 

$font${color Green}MEM   ${color Red}${memperc}%  ${color Green}${membar} 
$alignr${color Green}$mem / $memmax

${font Arial:bold:size=12}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color Green}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${color Red}${fs_used_perc /home}%
${color Green}${fs_bar /home}
$font${color Green}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${color Red}${fs_used_perc /}%
${color Green}${fs_bar /}
$font${color Green}/media/Storage $alignc ${fs_used /media/Storage} / ${fs_size /media/Storage} $alignr ${color Red}${fs_used_perc /media/Storage}%
${color Green}${fs_bar /media/Storage}
$font${color Green}/media/Backup $alignc ${fs_used /media/Backup} / ${fs_size /media/Backup} $alignr ${color Red}${fs_used_perc /media/Backup}%
${color Green}${fs_bar /media/Backup}

${font Arial:bold:size=12}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
$font${color Green}Name${alignr}CPU%  MEM%
${color Red}${top name 1} $alignr${top cpu 1}   ${top mem 1}
${color Green}${top name 2} $alignr${top cpu 2}   ${top mem 2}
${color Green}${top name 3} $alignr${top cpu 3}   ${top mem 3}

${font Arial:bold:size=12}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color Green}External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail} 
$font${color Green}Ethernet IP (${downspeedf eth0}k/s)$alignr ${addr eth0}
$font${color Green}Wi-Fi (${downspeedf wlan0}k/s)$alignr${addr wlan0}
$font${color Green}Strength$alignr ${wireless_link_qual wlan0}%

${font Arial:bold:size=12}${color Tan2}AMAROK${color DarkSlateGray}${hr 2}
$font${color Green}${color Red}${execi 30 ~/Computers/Bash/Conky/amarok.sh title}
$font${color Green}${execi 5 ~/Computers/Bash/Conky/amarok.sh artist}
$font${color Green}${execi 5 ~/Computers/Bash/Conky/amarok.sh album} ($font${color Green}${execi 5 ~/Computers/Bash/Conky/amarok.sh year})
$font${color Green}${execi 5 ~/Computers/Bash/Conky/amarok.sh genre}
$font${color Green}${execibar 5 ~/Computers/Bash/Conky/amarok.sh progress} 

${font Arial:bold:size=12}${color Tan1}GMAIL${color DarkSlateGray} ${hr 2}
$font${color Green}New Mail$alignc${font Arial:size=12}${color Red}${texeci 60 perl ~/Computers/Bash/Conky/gmail.pl n}
$font${color Green}${execi 60 perl ~/Computers/Bash/Conky/gmail.pl s}

```

I am having a couple of problems with this:

Firstly,

if you look at the following lines 
```

$font${color Green}Ethernet IP (${downspeedf eth0}k/s)$alignr ${addr eth0}
$font${color Green}Wi-Fi (${downspeedf wlan0}k/s)$alignr${addr wlan0}

```

You can see that I want the download speed (with decimals) in brackets next to the text Ethernet IP and Wi-Fi. If you look at the attached screenshot you can see that there is a weird extra space right after the numbers and before k/s.

It should read:
```

0.0 k/s

```

Instead it reads:
```

0.0  k/s

```

I just can't get rid of this space!!!!

The other issue is the External IP command:
```

$font${color Green}External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail} 

```

This runs the following in the terminal:
```

--2009-04-19 13:34:17--  http://whatismyip.org/
Resolving whatismyip.org... 75.147.234.41
Connecting to whatismyip.org|75.147.234.41|:80... connected.
HTTP request sent, awaiting response... 
Length: unspecified [text/plain]
Saving to: `STDOUT'

    [        <=>                            ] 14          2.27B/s   in 6.2s    

2009-04-19 13:38:03 (2.27 B/s) - `-' saved [14]

```

It is because of this command that conky takes AGES to start up. My internet isn't that slow and it should run it much faster, but for some reason I have to wait over 2-3 minutes before this command completes, and only then does conky start up. I can fix this slow start quite easily by removing the External IP command, however, I actually want to use that command as it is useful.

Also on occasion my internet may not be connected and so this command would entirely fail. Is there any way to get around theses issues?

---

### Post by unutbu on 2009-04-19
Save this as ~/bin/get-external-ip.sh
[PHP]
#!/bin/sh
dig +time=1 +retry=0 192.168.1.1 2>/dev/null 1>&2
if [ $? -eq 0 ]; then
    wget http://canyouseeme.org/ -O - 2>/dev/null | awk '/name="IP"/{if (gsub(/[^0-9.]+/,"")) {print}}  '
fi[/PHP]
The "dig" command checks if you have a connection to your router. Change 192.168.1.1 to the ip address of your router.

If you have a connection, this command will place its return value of 0 in $?. If there is no connection, then $? will have a non-zero value. 

The "wget http://canyouseeme.org" command gets your external ip. It might be faster than using whatismyip.org, which just appears to be slow.

Make it executable:
```

chmod 755 ~/bin/get-external-ip.sh
```

Change 
```

{execi 3600 wget -O - http://whatismyip.org/ | tail}
```

to 
```

{execi 3600 ~/bin/get-external-ip.sh}
```


PS. I found your tutorial on repacking debs [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396) a big time-saver recently. Thank you very very much. :P

---

### Post by abhiroopb on 2009-04-19
Thanks a lot for that.

Unfortunately, my router address changes a lot as I connect through various wi-fi hubs. Is there anyway for it figure out the ip address of the router each and every time? Without any input from me?

Glad it was helpful...for more tutorials you can check out my blog: ubuntuextreme.blogspot.com. I'm trying to find something new to post about, and I think it'll probably be a conky config file but going really in-depth as I spent all of yesterday learning what conky is!

Thanks again

---

### Post by unutbu on 2009-04-19
You can change 192.168.1.1 to something like google.com.
The dig command will simply check if it can reach that ip address or hostname.

PS. Very nice tuts at [http://ubuntuextreme.blogspot.com/](http://ubuntuextreme.blogspot.com/)! Thanks.

Edit: LOL, you can point dig at canyouseeme.org. That might make the most sense :)

---

### Post by abhiroopb on 2009-04-19
Thanks thats perfect!!

Any thoughts on that other strange spacing error?

---

### Post by unutbu on 2009-04-19
Nope, I tried, but I don't have the answer. 
"${downspeedf eth0}" seems to get replaced by a string with trailing spaces. If we could pipe that string to another command, then it could be fixed. But I don't know of a way to do that.

If it really bothers you, you might have to find another program to calculate download speed, or look into the conky source code.

But, then again, I don't know conky all that well. Perhaps there is an easier way...

---

### Post by abhiroopb on 2009-04-19
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

If you look at this website, the downspeedf is a frequently used command and no-one seems to be having trouble with it.

So, I'm wondering if its just a bug I have.

---

### Post by unutbu on 2009-04-19
Right you are. 

You can get rid of the trailing spaces by commenting out "use_spacer yes". See [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by abhiroopb on 2009-04-19
PERFECT!!

Ah things like that drive me crazy.

Glad you liked the tutorials. I'm interested in doing one about conky, but are there any other things it would be useful to write tutorials about?

I'm less interested about "general" ones, as there are already many many of those. I'd be keen on ideas which target very niche requirements (e.g. my guide on rsync, is very very specific, yet because its so specific its much easier to follow).

Any thoughts?

---

### Post by unutbu on 2009-04-19
Well, one thing that confuses the heck out of me is how to send email and receive gmail on a home machine behind a router, without a static external ip address, using emacs.
That's pretty specific, but I know emacs is not everyone's cup of tea.

I've sort of managed to get emacs email working, but finding all the information was difficult (not all in one place), and I still don't know if I did it properly or in the best way.

Sort of in the same vein, I would love to see a comparative description of the options for SMTP, MTA, SSL/TLS thingies on Ubuntu. There are so many of these packages, I just don't know which ones I need. (mailx, msmtp, ssmtp, esmpt, sendemail -- not to be confused with sendmail -- exim4, postfix, fetchmail, procmail...) Which ones are fungible? What happens if you install more than one MTA (e.g. exim4 and postfix)? Are there links to documentation on how to configure them all?

That's all I can think of right now. Feel free to take 'em or leave 'em. If I can think of anything else, I'll let you know.

Edit: Oh yes, I would also love to see a tutorial on how to setup an emacs interface to MySQL which replicates the functionality of phpmyadmin. Problem is, I don't know if such a thing exists... :)

---

