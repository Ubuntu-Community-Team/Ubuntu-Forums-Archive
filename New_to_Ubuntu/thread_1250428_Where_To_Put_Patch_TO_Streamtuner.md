---
title: "Where To Put Patch TO Streamtuner"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by zebraneo on 2009-08-26
I found the patch to Live365 streamtuner, but I have no idea where or how to install the patch.

---

### Post by Partyboi2 on 2009-08-28
Hi, to apply the patch download the streamtuner source from [[COLOR=Blue]here[/COLOR]]("http://freshmeat.net/urls/612ca693f56e461a3a8b82841f378b18") Then open a terminal (Applications>Accessories>Terminal) and change directory to where the downloaded streamtuner-0.99.99.tar.gz is, eg if its located on your Desktop
```
cd ~/Desktop
```
then extract it with
```
tar xvzf streamtuner-0.99.99.tar.gz
```
Then go [[COLOR=Blue]here[/COLOR]]("http://vectorlinux.osuosl.org/veclinux-5.8/old/source/streamtuner-0.99.99-live365.diff") and copy and paste the patch into gedit (Applications>Accessories>Text Editor) and save as streampatch and save it into the streamtuner-0.99.99 directory which should be on your Desktop (If you extracted the tar.gz to the Deskop)
Then in the terminal enter the streamtuner-0.99.99 directory
```
cd streamtuner-0.99.99
```
then apply the patch with
```
patch -p0 <streampatch
```
then compile with
```
./configure
make
sudo make install
```

---

