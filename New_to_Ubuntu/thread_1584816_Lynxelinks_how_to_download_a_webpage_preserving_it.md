---
title: "Lynx/elinks: how to download a webpage preserving its frame format ?"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-29
Hello,

I would like to make a pdf or a txt of a webpage

ok, let's take bbc news:

[http://www.bbc.co.uk/news/world/](http://www.bbc.co.uk/news/world/)

I get this using : elinks or lynx , some mess, example with another site ( :(
```

contres * [69]Généalogie * [70]Nautisme * [71]Location Vacances * [72]Solutions aux entreprises * [73]Votre page * [74]Votre blog * [75]Vos réactions * [76]Vos chroniques * [77]Votre classeur * [78]Découvrez l'Editions abonnés * [79]Vos alertes * [80]Vos dépêches * [81]Le debrief * [82]El Pais Plus * [83]Découvrez l'Editions abonnés * [84]Les articles du Monde * [85]Le journal électronique * [86]Les archives * [87]Les dessins * [88]Les photos du jour * [89]Découvrez l'Editions abonnés * [90]Check-list * [91]Que dit Le Monde ? * [92]La 12:15 * [93]La Toile de l'éducation * [94]Les coulisses de l'économie * [95]Découvrez l'Editions abonnés * [96]Dossiers * [97]Thématiques * [98]Repères * [99]Annales du bac * [100]Résultats du bac * [101]Fiches pays * [102]Base élections * [103]Découvrez l'Editions abonnés * [104]INTERNATIONAL * [105]AFRIQUE * [106]EUROPE * [107]AMERIQUES * [108]ASIE-PACIFIQUE * [109]PROCHE-ORIENT Les dépêches * [110]Exécution suspendue en Californie: les anti-peine de mort crient victoire 29/09 AFP Plusieurs associations américaines de défense des droits civils se montraient satisfaites mercredi de la suspension de l'exécution d'Albert Brown en Californie,... * [111]La Cour suprême des Etats-Unis à nouveau saisie par un détenu de Guantanamo 29/09 AFP Un détenu koweïtien de Guantanamo a saisi la Cour suprême des Etats-Unis pour protester contre l'interprétation faite par les tribunaux fédéraux, no20

```

tahnks if someone knows

---

### Post by duanedesign on 2010-10-01
There are Add-ons for Firefox that might help you with this.
[Here is an example.]("https://addons.mozilla.org/en-US/firefox/addon/636/")

I have also used wget to download web pages before. Here are my notes on that. They are a bit messy, you might have better luck by running 'man wget' in a Terminal.

Download an entire website
> wget -r -p -e robots=off -U mozilla  [http://people.ubuntu.com/~billy/graphs/](http://people.ubuntu.com/~billy/graphs/)    --limit-rate=20k : Limits the rate at which it downloads files. (20Kb/s) -o $HOME/wget_log.txt

wget -r  -l 2 robots=off -U mozilla  [http://people.ubuntu.com/~billy/graphs/plots](http://people.ubuntu.com/~billy/graphs/plots) 

wget -r -p -e robots=off -U mozilla  [http://people.ubuntu.com/~billy/graphs/](http://people.ubuntu.com/~billy/graphs/) --include directories=ubuntuone-client

wget --random-wait -r -p -e robots=off -U mozilla [http://www.example.com](http://www.example.com)

-p parameter tells wget to include all files, including images.
-e robots=off you don't want wget to obey by the robots.txt file
-U mozilla as your browsers identity.
--random-wait to let wget chose a  random number of seconds to wait, avoid get into black list.
Other Useful wget Parameters:
--limit-rate=20k limits the rate at which it downloads files.
-b continues wget after logging out.
-o $HOME/wget_log.txt logs the output

best of luck.
duanedesign

---

### Post by honeybear on 2010-10-01
Thanks so much !

---

### Post by Paddy Landau on 2010-10-01
> **honeybear said:**
> I would like to make a pdf or a txt of a webpage
I'm a little confused. If you make a txt file, you will lose all formatting, completely.

If you want to save a web page so that you can view it later, exactly as intended, you need to save the entire page. You can do this with the MHT format (for Firefox, use the [UnMHT add-on]("https://addons.mozilla.org/en-US/firefox/addon/8051/")).

Or, as duanedesign said, use [Firefox's PDF add-on]("https://addons.mozilla.org/en-US/firefox/addon/636/").

---

