---
title: "Internet explorer 8 and Wine"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ryon341 on 2009-11-08
I need to run IE from Ubuntu 9.1.  I received a lot of help in another thread.  I'm, apparently, missing a step somewhere.

I loaded Wine from the Software Center. It appeared to load correctly. I downloaded the IE8 from the link given by Hankinator. When I right-click the link and choose "open with Wine Windows Program Loader", I receive the response:

Unable to find a volume for program extraction.  Please verify that you have proper permissions.

What am I missing?

---

### Post by gdonwallace on 2009-11-08
Check the permissions on that file.  It could be that they are not set correfctly for read / write / execute for all users.  

I have not used Wine in a while, but you might check to see if there is an option to install a windows program from an alternate source and point it to the download.  That may fix the permissions problem that it sounds like you are having.

---

### Post by BewareOfDog on 2009-11-14
Same exact problem here, and I followed the installation instructions to the letter:

[http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html]("http://wine-review.blogspot.com/2009/11/internet-explorer-8-on-linux-with-wine.html")

---

### Post by bumanie on 2009-11-14
If the IE8 download is on your desktop, are you changing your directory to desktop before trying to install? If it is on your desktop > cd ~/Desktop hit enter and then type the command - if in another directory, cd <to that directory>

---

### Post by Sir Jasper on 2009-11-14
Hi,

When it is installed and tested would you guys please be so kind as to say how well it works and also which version of Wine you are using?

My regards

---

### Post by sandyd on 2009-11-14
type this into the terminal
```

cd /usr/bin
sudo wget  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 /usr/bin/winetricks
winetricks volnum

```

---

### Post by BewareOfDog on 2009-11-15
> **carlee said:**
> type this into the terminal
```

cd /usr/bin
sudo wget  [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
sudo chmod 777 /usr/bin/winetricks
winetricks volnum

```


Thank you. That got me to the next step, but now I get a message
"Setup could not verify the integrity of files needed for installation.
Make sure the cryptograp"

Then it stops there. I don't even need to install IE8 - (I thought I did for a certain web page but I found a way to make it work right in Firefox) Its just the learning process and curiosity that has peaked my interest with this. Thanks for the advice.

---

### Post by Sir Jasper on 2009-11-15
Hi,

I installed Internet Explorer 6 via Wine-Doors and it works quickly and well.
Firefox Portable version 3.5.5 also works well in Wine. I only mention this as it can be tried (on 9.04 and earlier) and then merely deleted if not required or the Ubuntu version is installed.

My regards

---

### Post by sandyd on 2009-11-15
> **BewareOfDog said:**
> Thank you. That got me to the next step, but now I get a message
"Setup could not verify the integrity of files needed for installation.
Make sure the cryptograp"

Then it stops there. I don't even need to install IE8 - (I thought I did for a certain web page but I found a way to make it work right in Firefox) Its just the learning process and curiosity that has peaked my interest with this. Thanks for the advice.
heres the full instructions....
```

sudo mkdir /wine
sudo chmod 777 /wine
sudo chown yourusername /wine
WINEPREFIX=/wine/ie6 winecfg
```
replace "yourusername" with your username
go to the libraries tab

```

" browseui="native, builtin"
"crypt32"="native, builtin"
"gdiplus"="native"
"hhctrl.ocx"="native, builtin"
"hlink"="native, builtin"
"iernonce"="native, builtin"
"iexplore.exe"="native, builtin"
"itircl"="native, builtin"
"itss"="native, builtin"
"jscript"="native, builtin"
"mlang"="native, builtin"
"mshtml"="native, builtin"
"msimtf"="native,builtin"
"msxml3"="native,builtin"
"riched20"="native,builtin"
"riched32"="native,builtin"
"secur32"="native, builtin"
"shdoclc"="native, builtin"
"shdocvw"="native, builtin"
"shlwapi"="native, builtin"
"url"="native, builtin"
"urlmon"="native, builtin"
"usp10"="native, builtin"
"uxtheme"="native,builtin"
"wininet"="builtin"
"wintrust"="native, builtin"
"xmllite"="native, builtin"

```type the first part (for example, xmllite) in the "add new override" box
for those that have only "builtin" you need to click on the library after you add the override and select edit. change it to "builtin"
same thing needs to be done for those that only have "native"

get these files from the C:\windows\system32 folder of a winxp machine
```

msctf.dll
msimtf.dll
uxtheme.dll

```copy them to your desktop

then run this
```

cd ~/Desktop
mv *dll /wine/ie8/drive_c/windows/system32
winetricks allfonts gdiplus msls31 msxml3 riched20 riched32 tahoma fontfix fontsmooth-rgb
cd ~/
wget -c http://www.microsoft.com/downloads/info.aspx?na=90&p=&SrcDisplayLang=en&SrcCategoryId=&SrcFamilyId=341c2ad5-8c3d-4347-8c03-08cdecd8852b&u=http%3a%2f%2fdownload.microsoft.com%2fdownload%2fC%2fC%2f0%2fCC0BD555-33DD-411E-936B-73AC6F95AE11%2fIE8-WindowsXP-x86-ENU.exe
WINEPREFIX=/wine/ie8 wine IE8-WindowsXP-x86-ENU.exe
```might have some typos in the script cause' im typing this from a portable music performance stage (on wheels..... and only the blue lights are on....)

---

### Post by GH68 on 2009-11-17
Thanks for the instruction, Carlee. I followed the instructions and it looked ok until the last line where I get a dialogue box saying "Extraction Failed - Unable to find a volume for file extraction. Please verify that you have proper permissions".

I also wonder if "WINEPREFIX=/wine/ie6 winecfg" should be "WINEPREFIX=/wine/ie8 winecfg" in your instruction? However, this is likely not causing my problem.

---

### Post by NickJones on 2009-11-17
It can be installed through PlayOnLinux, it makes the setup a whole lot easier.

---

### Post by GH68 on 2009-11-18
> **NickJones said:**
> It can be installed through PlayOnLinux, it makes the setup a whole lot easier.

Thanks Nick! I installed IE6 using PlayOnLinux and it was really simple.

---

### Post by harish.bhamare on 2010-07-31
> **carlee said:**
> heres the full instructions....
```

sudo mkdir /wine
sudo chmod 777 /wine
sudo chown yourusername /wine
WINEPREFIX=/wine/ie6 winecfg
```replace "yourusername" with your username
go to the libraries tab

```

" browseui="native, builtin"
"crypt32"="native, builtin"
"gdiplus"="native"
"hhctrl.ocx"="native, builtin"
"hlink"="native, builtin"
"iernonce"="native, builtin"
"iexplore.exe"="native, builtin"
"itircl"="native, builtin"
"itss"="native, builtin"
"jscript"="native, builtin"
"mlang"="native, builtin"
"mshtml"="native, builtin"
"msimtf"="native,builtin"
"msxml3"="native,builtin"
"riched20"="native,builtin"
"riched32"="native,builtin"
"secur32"="native, builtin"
"shdoclc"="native, builtin"
"shdocvw"="native, builtin"
"shlwapi"="native, builtin"
"url"="native, builtin"
"urlmon"="native, builtin"
"usp10"="native, builtin"
"uxtheme"="native,builtin"
"wininet"="builtin"
"wintrust"="native, builtin"
"xmllite"="native, builtin"

```type the first part (for example, xmllite) in the "add new override" box
for those that have only "builtin" you need to click on the library after you add the override and select edit. change it to "builtin"
same thing needs to be done for those that only have "native"

get these files from the C:\windows\system32 folder of a winxp machine
```

msctf.dll
msimtf.dll
uxtheme.dll

```copy them to your desktop

then run this
```

cd ~/Desktop
mv *dll /wine/ie8/drive_c/windows/system32
winetricks allfonts gdiplus msls31 msxml3 riched20 riched32 tahoma fontfix fontsmooth-rgb
cd ~/
wget -c http://www.microsoft.com/downloads/info.aspx?na=90&p=&SrcDisplayLang=en&SrcCategoryId=&SrcFamilyId=341c2ad5-8c3d-4347-8c03-08cdecd8852b&u=http%3a%2f%2fdownload.microsoft.com%2fdownload%2fC%2fC%2f0%2fCC0BD555-33DD-411E-936B-73AC6F95AE11%2fIE8-WindowsXP-x86-ENU.exe
WINEPREFIX=/wine/ie8 wine IE8-WindowsXP-x86-ENU.exe
```might have some typos in the script cause' im typing this from a portable music performance stage (on wheels..... and only the blue lights are on....)


Hello,
I am able to use IE8 good with WINE....
But I would like to install IE8 without WINE..
Suppose we didn't ..... so can you suggest me similar application for the IE8 for Linux/Ubuntu..
Please help.
Thanx.

---

### Post by Mark Phelps on 2010-07-31
> **harish.bhamare said:**
> Hello,
I am able to use IE8 good with WINE....
But I would like to install IE8 without WINE..
Suppose we didn't ..... so can you suggest me similar application for the IE8 for Linux/Ubuntu..
Please help.
Thanx.

You also posted this in another thread.  That is considered double-posting.

Please do NOT do that.

---

