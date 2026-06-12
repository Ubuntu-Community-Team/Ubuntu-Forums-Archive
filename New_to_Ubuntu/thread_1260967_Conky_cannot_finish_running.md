---
title: "Conky cannot finish running"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by rabien on 2009-09-08
> rabien@ubuntu:~$ conky
Conky: unknown variable 
Conky: desktop window (1800065) is subwindow of root window (1a7)
Conky: window type - override
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
*** buffer overflow detected ***: conky terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7cb4da8]
/lib/tls/i686/cmov/libc.so.6[0xb7cb2eb0]
/lib/tls/i686/cmov/libc.so.6[0xb7cb2495]
conky[0x805d4d9]
conky[0x805d7b1]
conky[0x8062355]
conky[0x8063308]
conky[0x8064b05]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7bcd775]
conky[0x804c471]
======= Memory map: ========
08048000-0807f000 r-xp 00000000 07:00 848331     /usr/bin/conky
0807f000-08080000 r--p 00036000 07:00 848331     /usr/bin/conky
08080000-08081000 rw-p 00037000 07:00 848331     /usr/bin/conky
08081000-0808e000 rw-p 08081000 00:00 0 
0821f000-082c8000 rw-p 0821f000 00:00 0          [heap]
b75c3000-b75e4000 r--p 00000000 07:00 2336       /usr/share/fonts/truetype/ttf-liberation/LiberationSans-Bold.ttf
b75e4000-b75f0000 r--p 00000000 07:00 828533     /home/rabien/.fonts/Radiof.ttf
b75f0000-b75f7000 r--p 00000000 07:00 835604     /home/rabien/.fonts/weather.ttf
b75f7000-b7669000 r--p 00000000 07:00 984480     /usr/share/fonts/truetype/freefont/FreeSans.ttf
b767a000-b7687000 r-xp 00000000 07:00 196673     /lib/libgcc_s.so.1
b7687000-b7688000 r--p 0000c000 07:00 196673     /lib/libgcc_s.so.1
b7688000-b7689000 rw-p 0000d000 07:00 196673     /lib/libgcc_s.so.1
b7689000-b768a000 r--p 00000000 07:00 870256     /usr/lib/locale/en_US.utf8/LC_TIME
b76a4000-b76c7000 r--p 00000000 07:00 795251     /home/rabien/.fonts/verdana.ttf
b76c7000-b76cd000 r--s 00000000 07:00 594950     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b76cd000-b76cf000 r--s 00000000 07:00 595550     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
b76cf000-b76d2000 r--s 00000000 07:00 595549     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b76d2000-b76d5000 r--s 00000000 07:00 595547     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b76d5000-b76d6000 r--s 00000000 07:00 595518     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b76d6000-b76d9000 r--s 00000000 07:00 595517     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b76d9000-b76e0000 r--s 00000000 07:00 595507     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b76e0000-b76e3000 r--s 00000000 07:00 595506     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b76e3000-b76eb000 r--s 00000000 07:00 595486     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b76eb000-b76f6000 r--s 00000000 07:00 595483     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b76f6000-b76f8000 r--s 00000000 07:00 595328     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b76f8000-b76f9000 r--s 00000000 07:00 595326     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b76f9000-b771b000 r--s 00000000 07:00 595322     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b771b000-b7722000 r--s 00000000 07:00 595320     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7722000-b7723000 r--s 00000000 07:00 595308     /var/cache/fontconfig/6c0172a5813a6f17430f4af3a6ca3fa0-x86.cache-2
b7723000-b772e000 r--s 00000000 07:00 595287     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b772e000-b7731000 r--s 00000000 07:00 589911     /var/cache/fontconfig/cabbd14511b9e8a55e92af97fb3a0461-x86.cache-2
b7731000-b7738000 r--s 00000000 07:00 593337     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7738000-b773e000 r--s 00000000 07:00 595219     /var/cache/fontconfig/4ab6955e758771a69a37996afd2e356b-x86.cache-2
b773e000-b7740000 r--s 00000000 07:00 593980     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b7740000-b7744000 r--s 00000000 07:00 591098     /var/cache/fontconfig/19824189c69f451d43f067fe3ed0222a-x86.cache-2
b7744000-b7762000 r--s 00000000 07:00 595187     /var/cache/fontconfig/da4ff94c2d5898ec49ad21bff50a47e2-x86.cache-2
b7762000-b77a1000 r--p 00000000 07:00 870248Aborted
This is what I get when I run conky, it doesn't complete and i have no idea which line of which script did it get aborted for.

This is my conkyrc script.
> use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t${color}${font}


${color BADCDD}${font Poky:size=18}S${font}${goto 46}${voffset -8}Kernel:  ${alignr}${kernel}${color}
${goto 46}Uptime: ${alignr}${uptime}
${font Poky:size=18}y${font}${goto 46}${voffset -8}Temperature: ${execi 120 hddtemp /dev/sda -n --unit=C}°C${alignr}Maxtor
${goto 46}${execpi 30 ~/scripts/hd_default.py}
${font Poky:size=18}P${font}${offset -19}${voffset 9}${voffset -15}${goto 46}CPU1: ${cpu cpu1}%${alignr}${color2}${cpugraph cpu1 8,50 CE5C00 E07A1F}${color}
${font Poky:size=18}M${font}${goto 46}${voffset -7}RAM: $memperc%
${offset 1}${voffset 3}${membar 4,18}${goto 46}${voffset -4}U: ${mem} F: ${memeasyfree}
${font Poky:size=18}a${font}${goto 46}${voffset -10}Processes: ${alignr 30}CPU${alignr}RAM$
${voffset -1}${goto 50}${color2}${top name 1}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 130}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 50}${color2}${top name 2}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 130}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 50}${color2}${top name 3}${color}${font Liberation Sans:style=Bold:size=8}${color1} ${goto 130}${top cpu 3}${alignr }${top mem 3}${color}${font}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py username password 3}${color}

${color C2E078}
${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

 ${font Radio Space:size=14}${time %A %d %Y}${font}
    ${font Radio Space:size=55}${time %H:%M}${font}${color}can anyone help me with this? thanks! I kind of meddled with 2 scripts and now I don't know which part went wrong cos i don't speak python :s

---

### Post by arochester on 2009-09-08
You could try posting to [http://linux-hardcore.com/index.php?board=80.0](http://linux-hardcore.com/index.php?board=80.0)

---

### Post by rabien on 2009-09-08
okay =) thanks alot!

---

