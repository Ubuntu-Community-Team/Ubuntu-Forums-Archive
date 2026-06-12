---
title: "Php Scripts??"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by ENigma885 on 2008-12-25
I have just downloaded a program needed in some of my clinical assays; [[COLOR="Red"]**_bioGraph_**[/COLOR]]("http://downloads.sourceforge.net/biograph/bioGraph_1.0.zip?modtime=1175679115&big_mirror=0") (Click to download)
But the program contains php script files that i have no idea how to deal with.
When i open them in Firefox i got "Openwith or Save as dialog"
One of the program requirements is "Apache webserver with PHP support"
i think that's wat i missed. Synaptic search results contain many related packages i have no clue which is needed.

Any help will be appreciated? 
(OS Ubuntu 8.04 Desktop)

---

### Post by marshall.robert on 2008-12-25
ill give you some command line parameters, since its easier to give you them than explain the point and click method.

```

sudo apt-get install apache2 php5

```

then once that is installed

```

sudo chown -R Username /var/www/
ln -s /var/www/ ~/webdir

```

that will sort you out with what you should need and enable you to easily place files in the required folder, along with a link to said folder named "webdir" which will appear in your home folder.

if i havnt been clear, let me know and ill better try to exlain

-rob

---

### Post by ENigma885 on 2008-12-25
*Thanks marshall *=) Just before i noticed ur reply. A buddy helped me online.
i'm not sure if i understand every step but here's wat i did:-
**1. **Installed Apache, PHP5, Imagemagick, and Gnuplot.
**2.** Checked Apache with [http://localhost/](http://localhost/) and i got "It works!".
**3.** ```
cd /var/www
```
**4.** ```
sudo chmod 777 .
```
**5.** Copied bioGraph extracted folder to /var/www
**6.** In an internet browser, probably Firefox, paste "http://localhost/bioGraph_1.0/"
**7.** Using ```
whereis gnuplot
``` and ```
whereis convert
``` to localize gnuplot and convert to c if there's a need to modify config.php
and in my case the defaults works fine;  /usr/bin/gnuplot and /usr/bin/convert correct places.
**8.** 1st run i got error log containing something like ```
Warning: chdir() [function.chdir]: No such file or directory (errno 2) in /var/www/bioGraph_1.0/mmgraph.php on line 32
Warning: fopen(/home/vimal/public_html/biograph/upload/tmp/file4646.dat) [function.fopen]: failed to open stream: No such file or directory in /var/www/bioGraph_1.0/mmgraph.php on line 34
```
**9.** In Terminal window ```
sudo gedit /var/www/bioGraph_1.0/config.php
```
Edited the temporary directories, last 3 lines, to ```
$TMP_DIR ="/var/www/bioGraph_1.0/tmp";

$CACHE_DIR ="/var/www/bioGraph_1.0/cache";

$URL_PATH = "http://localhost/bioGraph_1.0/cache";
```
**10.** WORKED PERFECTLY

---

