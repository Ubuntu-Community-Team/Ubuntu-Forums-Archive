---
title: "installing applications not listed in &quot;add/remove&quot;"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by patocardo on 2009-04-08
Hi:
  I am trying to view dwg files, so I downloaded lx_viewer-1.0.3.tar.gz, and uncompressed it, there are no .deb or .rmp files, nor I can run Terminal on the folder (I don't know how to do that)
  I also tried to search "dwg" in the "add/remove" (synaptics I think it is), with no result.
  I looking for a free app, so VariCAD and other cads are not solution for now.

---

### Post by acimmarusti on 2009-04-08
From the FAQ's of the LX-viewer website:

> Q: Do I need additional files from the OpenDWG Alliance?

A: That depends. If you plan to compile the program from the source files then the answer is yes. You will need the files ad2.a and ad3.a for Linux which are available from the OpenDWG alliance. It will be necessary for you to become a member of the alliance, but membership is free so long as you are using the files for personal use or for use internally within your own company. After you download these files copy or move ad2.a and ad3.a into the subdirectory OpenDWG which should be created when you expand the Lx-Viewer tar.gz archive.

When you download the libraries from OpenDWG there will be lots of header files plus examples included. Do not use any of the header files with LX-Viewer. We supply our own versions, many of which have the same names as the OpenDWG header files, but with different content.

Yes, you've just downloaded the source of the program. Thus, to make it work, you need to compile and build it. Don't be scared, get the files from OpenDWG as described above and just follow these instructions and it should work:

```

mkdir Source
cd Source/
tar xvfz lx_viewer-1.0.3.tar.gz
cd lx_viewer-1.0.3
mkdir OpenDWG
mv .../wherever_you_put_the_OpenDWG_files/ad*.a OpenDWG
./configure
make
sudo make install
make clean

```

Then you are done. The make command could take a while. If you receive errors let me know.

---

### Post by patocardo on 2009-04-08
Thank you very much but
> **acimmarusti said:**
> 
mv .../wherever_you_put_the_OpenDWG_files/ad*.a OpenDWG


This command does not work, it returns:
```

mv: no se puede efectuar `stat' sobre «ad*.a»: No existe el fichero ó directorio

```
That means: "it cannot be done 'stat' over «ad*.a»: file or dir doesn't exist"

---

### Post by durand on 2009-04-08
You need to actually change it to where you put the files.
```
mv .../wherever_you_put_the_OpenDWG_files/ad*.a OpenDWG
```
is a placeholder. Replace "wherever_you_put_the_OpenDWF_files" with the actual location.

---

### Post by Wobblybob on 2009-04-08
> **acimmarusti said:**
> 

```


mv .../wherever_you_put_the_OpenDWG_files/ad*.a OpenDWG

```


This line of code needs you to add the location of the 2 extra files ad1.a and ad2.a that you have downloaded from the website. So if you stored them in your home directory at  /home/patocardo you would need to type 

mv /home/patocardo/ad*.a /home/patocardo/Source/lx_viewer-1.0.3/OpenDWG

to put them in the /home/patocardo/Source/OpenDWG directory that you have created.

---

### Post by acimmarusti on 2009-04-08
Instead of using that line just move the ad2.a and ad3.a files (that you previously downloaded) into the OpenDWG directory created under lx_viewer-1.0.3, then follow the rest of the steps.

No need to translate Spanish to me, I'm from Venezuela, but for the sake of the forum lets keep it in English (except for the terminal messages you may get)

---

### Post by kogos on 2009-06-23
Unfortunately, ad2.a and ad3.a files are not free anymore, since there is no free subscription anymore in  [http://www.opendwg.org/](http://www.opendwg.org/) as i see... So, i guess noone will download LX-viewer now....

---

### Post by acimmarusti on 2009-06-23
fear not: [http://www.fsf.org/campaigns/priority.html#opendwgreplacement](http://www.fsf.org/campaigns/priority.html#opendwgreplacement)

---

### Post by voxra on 2009-06-26
> **acimmarusti said:**
> fear not: [http://www.fsf.org/campaigns/priority.html#opendwgreplacement](http://www.fsf.org/campaigns/priority.html#opendwgreplacement)
The information in your link states: "There are a number of free software design programs that can manipulate CAD files.", but it doesn't link to any (unless I'm not reading it correctly)?

---

