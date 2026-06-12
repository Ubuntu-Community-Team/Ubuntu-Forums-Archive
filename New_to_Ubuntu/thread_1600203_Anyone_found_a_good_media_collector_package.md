---
title: "Anyone found a good media collector package?"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by JamButty on 2010-10-18
Has anyone found a reliable package for cataloging media collections? I have used Collectorz on Windows for years for my audio files collection and need a way to transfer prior data (years of corrections, assembling) to a new linux compatible package. I have been digging for a while and not found such. The closest so far is Tellico, but that does not look to be Ubuntu compatible. Collectorz via Wine does not work. Others have suggested VMWare, but that is just another form of Windows and the aim is to wean myself off MS entirely.

---

### Post by Melon Bread on 2010-10-18
[http://linuxappfinder.com/databases/collectionmanagers](http://linuxappfinder.com/databases/collectionmanagers)
Might wanna look there

---

### Post by JamButty on 2010-10-18
Will check them out. thanks!

---

### Post by JamButty on 2010-10-19
Just for the record, results of looking at above referenced packages -
========================
     Tellico      - by far the most promising. Appealing layout. Does a good job of pulling data from file metadata, but in a day of testing with many different csv files, small and large, after chopping up 7 years of accumulated data into little chunks to feed the import attempts, 4 separate installations, could not get a viable result. Just crashed every time. "help" option is just a standard KDE guide. Every bug report attempt generates a "this information is probably not useful" message, then craps out on install of additional debug modules. Maybe KDE/Gnome conflicts?

    Griffith     - movies
    GCstar     - no import possibility (other than file metadata)
    Katalog     - incompatible with Gnome
    aviManager - Movies
    Alexandria     - books only - data pulled only from web DBs

    Data Crow     - looks promising, but per [http://wiki.links2linux.de/wiki/PackMan_repo_instructions_for_Debian/Ubuntu](http://wiki.links2linux.de/wiki/PackMan_repo_instructions_for_Debian/Ubuntu)
                        nothing available for Ubuntu - only Open SuSe found.

    vMovieDB     - movies only - data pulled only from web DBs
    CdCat           - incompatible with Gnome
    Evergreen     - books only - data pulled only from web DBs
    GTKtalog     - no import possibility (other than file metadata)
========================
So still nothing at this point. If I ever get comfortable enough with Ubuntu that I could switch from a Gnome to a KDE environment without hopelessly complicating things, I might revisit some of these.

Does anyone have experience with importing into Tellico  from files (csv, PDF, XML) in a Gnome environment?

---

### Post by cariboo on 2010-10-19
> Data Crow - looks promising, but per [http://wiki.links2linux.de/wiki/Pack..._Debian/Ubuntu](http://wiki.links2linux.de/wiki/Pack..._Debian/Ubuntu)
nothing available for Ubuntu - only Open SuSe found.

Data Crow is a java applet, it will install on any distribution. Just download the installer, extract it to whereever you want. CD into the directory where you extract the zip file, make the installer executeable:

```
chmod +x installer.sh
```

Then run the script. It needs to be run as root as it installs to /usr/local/Data Crow:

```
sudo ./installer.sh
```

Once the program is installed cd into /usr/local/Data Crow:

```
cd /usr/local/Data*
```

The directory name has a space in it hence the wildcard. Make the datacrow script executable:

```
sudo chmod +x datacrow.sh
```

Then run the program as root:

```
sudo ./datacrow.sh
```

---

### Post by JamButty on 2010-10-19
Thanks! Up and running on Data Crow. Will report back with results.

---

### Post by JamButty on 2010-10-20
Imports from CSV are working in Data Crow! Oddly slow (up to 40 seconds per added record), but I can live with that for this initial transfer of data. In the future, a few records at a time directly from file metadata and/or web-based data sources will go faster. So far, seems a stable package. Will take a while to figure out all the bells and whistles - there's  a lot of them.

---

### Post by JamButty on 2010-11-17
Just an update - after trying to make Data Crow work for nearly a month I gave up. Was running it almost 24/7. A thousand record csv file would take 8-10 hours to import. Starting it up would take 10-15 minutes. Each keystroke (expanding, editing etc.) would take 30-60 seconds to enact. Not kidding. It looks highly customizable, so maybe it works for people with many collections with just a hundred records or so each. Much larger than that and it is really not usable.
Decided to bite the bullet and consolidate/correct all metadata as needed and reburn to DVDs for my whole collection. Found Tellico to be the best solution for this purpose. Fast, intuitive and reliable, as long as the metadata is kosher (make sure all track field data is there!)

---

