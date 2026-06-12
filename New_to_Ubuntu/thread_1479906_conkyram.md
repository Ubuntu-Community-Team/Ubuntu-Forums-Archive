---
title: "conky/ram"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by dzon65 on 2010-05-11
Trying to get this conky wright.The ram's usage in conky  doesn't show what's actually happening.No idea how to fix this.Added my rc and a screenshot.
Thanks in advance.
# Configuration de Conky
#
# la liste des variables a été enlevée de ce fichier en faveur
# de la documentation.
# Visitez [http://conky.sf.net](http://conky.sf.net) pour une liste à jour.

# La "zone de texte" est la fenêtre Conky (et non uniquement le texte).

# Mettez yes si vous voulez que Conky soit intégré à l'arrière plan
background yes

# Police de X quand Xft est désactivé, vous pouvez en choisir une avec le programme xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Utiliser Xft?
use_xft yes

# Police de Xft quand Xft est activé
xftfont Radio Space:size=8

# Texte alpha quand Xft est utilisé
xftalpha 0.8

# MPD hôte/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Tout imprimer vers console ?
out_to_console no

# Boîte mail (? : mail spool)
mail_spool $MAIL

# Intervalles de mises à jour en secondes
update_interval 0.50

# Ceci est le nombre de fois que Conky va se mettre à jour avant de quitter
# Mettre à zéro pour faire tourner en permanence
total_run_times 0

# Créer sa propre fenêtre au lieu d'utiliser le bureau (requis dans Nautilus) ?
own_window yes

# Si own_window est sur yes, vous pouvez utiliser les options normal, desktop ou override
own_window_type normal

# Utiliser le fond transparent avec own_window ?
own_window_transparent yes

# Si own_window_transparent est sur no, vous pouvez changer la couleur de fond ici
own_window_colour hotpink

# Si own_window est sur yes, ces options du gestionnaire de fenêtre peuvent être utilisées
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Utiliser le double buffering (réduit le scintillement, peut ne pas fonctionner avec tout le monde) ?
double_buffer yes

# Taille minimum de la zone de texte
minimum_size 150 100

# Dessiner les ombres ?
draw_shades no

# Dessiner les contours ?
draw_outline no

# Dessiner les bordures autour du texte ?
draw_borders no

# Dessiner les bordures autour des graphes ?
draw_graph_borders no

# Longueur des traits des séparateurs
stippled_borders 10

# Marge entre la bordure et le texte
border_margin 4

# Épaisseur de la bordure
border_width 1

# Couleur par défaut et couleur de la bordure
default_color white
default_shade_color black
default_outline_color black


# Espace entre les bords d'écran et le texte
# same thing as passing -x at command line (aucune idée de comment traduire ceci)
gap_x 12
gap_y 60

# Soustraire les buffers du système de fichiers de la mémoire utilisée (? :subtract file system buffers from used memory) ?
no_buffers no

# Mettez yes si vous voulez que tout le texte soit en majuscules
uppercase no

# Nombre d'échantillons CPU pour faire la moyenne
# Mettre sur 1 pour désactiver la moyenne
cpu_avg_samples 2

# Nombre d'échantillons réseau pour faire la moyenne
# Mettre sur 1 pour désactiver la moyenne
net_avg_samples 1

# Forcer UTF8 ? À noter que le support UTF8 requiert XFT
override_utf8_locale no

# Ajouter des espaces pour empêcher les objets de partir n'importe où ? Ceci affecte seulement certains objets
use_spacer none

# Autoriser chaque moniteur de port à suivre au plus tant de connections (si 0 ou not est mis, le nombre par défaut est 256) ?
#max_port_monitor_connections 256

# Nombre maximum d'objets spéciaux, ex : polices, décalages, alignements, etc. Pas bien compris ça moi...
#max_specials 512

# Taille maximum du buffer utilisateur pour le texte, c'est à dire sous la ligne TEXT
#max_user_text 16384

# Intervalle de mise à jour pour le démon du lecteur de musique, ex : mpd, audacious
#music_player_interval 3

# La variable est donnée soit au format $variable soit au format ${variable}. Cette dernière
# permet les caractères justes après la variable et doit être utilisée dans les
# trucs du réseau à cause d'un argument.

# Ce qui est placé après 'TEXT' apparaîtra à l'écran.


# Alignement du texte, les autres options possibles sont expliquées (sûrement sur le site web)
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_middle
#alignment top_middle
#alignment middle_left
#alignment middle_right
#alignment bottom_right
#alignment none


TEXT
${color #FF8000}SYSTEM ${color #232323}${hr 2}

${color #1992D6}CPU1: ${color #D4D5DB}${cpu cpu1}% ${alignr}
${cpubar cpu1 7,200}

${color #1992D6}CPU2: ${color #D4D5DB}${cpu cpu2}% ${alignr}
${cpubar cpu2 7,200}

${color #1992D6}RAM: ${color #D4D5DB} $memperc% ${alignr}
${membar 7,200}

${color #FF8000} HD ${color #232323}${hr 2}

${color #1992D6}${voffset -5}Home:
${voffset 4}${color #D4D5DB}${fs_free /home}/${fs_size /home} ${alignr}
${color #D4D5DB}${fs_bar 7,200 /home}
${if_mounted /media/disk}/80Gio   ${fs_used /media/disk}/${fs_size /media/disk}${alignr}${fs_used_perc /media/disk}%
${fs_bar /media/disk}
$endif
${color lightgrey}I/O disque :${color #D4D5DB} $diskio $color
${diskiograph 30,200 D4D5DB D4D5DB}

${color #D4D5DB}Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

${color #D4D5DB}Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color #FF8000}NETWORK ${color #232323}${hr 2}${color}

${color #D4D5DB}Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,100} ${alignr}${upspeedgraph eth0 25,100}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}


${color #1992D6}Signal: ${color #D4D5DB}${wireless_link_qual_perc wlan1} ${wireless_link_bar wlan1}

${color #FF8000}SYNAPTIC ${color #232323 }${color #232323}${hr 2}
${color #D4D5DB}${execi 1800 aptitude search "~U" | wc -l | tail} Updates


${color #FF8000}TIME ${color #232323}${hr 2}
${color #D4D5DB}${alignc 17}${font Arial Black:size=16}${time %H:%M}${font}

---

### Post by ankspo71 on 2010-05-11
Hi, I was having the same problem using conky too. The trouble is that membar and memperc shows "cached" plus used memory combined (not the actual used memory).

If you run the command "free -m" from the terminal, you can see how conky is interpreting the memory usage.

```
james@Jamess:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       [COLOR="Red"]1234[/COLOR]        777          0        141        634
-/+ buffers/cache:       [COLOR="Blue"]458[/COLOR]       1553
Swap:         4000          0       4000
```

Red = the used plus cached memory
Blue = the actual used memory

I'm not aware of any commands to use that would tell conky to show "used" memory only. If anyone knows, let us know :)

---

### Post by dzon65 on 2010-05-11
Been busting my b.... on this.Thanks and indeed,if someone knows...

---

