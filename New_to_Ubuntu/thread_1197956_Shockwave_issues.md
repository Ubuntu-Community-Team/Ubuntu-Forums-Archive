---
title: "Shockwave issues"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by m_ad on 2009-06-26
I followed the directions on [this]("https://help.ubuntu.com/community/Shockwave") page, and I _thought_ I had a working version of shockwave for firefox under windows. When I tried to use mozplugger and attempt to test the shockwave player, I just get a blank page.

I know I'm not explaining this well, but firefox isn't telling me it needs a plugin. Instead, it's just a blank page.

---

### Post by Zzl1xndd on 2009-06-26
To insure you are launching the Windows Version of Firefox and not the Linux one correct?

---

### Post by m_ad on 2009-06-26
I thought that guide allowed you to integrate the windows plugin into the linux firefox. Maybe I read it wrong.

I included 2 screenshots, the first being what is shown using the windows firefox with the shockwave player installed, and the second being the linux version.

Apparently it wants me to save some file.

EDIT: the "Adobe shockwave player is now installing" will sit for 20 mins and do nothing.

---

### Post by m_ad on 2009-06-28
any help would be appreciated

---

### Post by &#1082;&#1086;&#1084;&#1084;&#1091;&#1085;&#1080;&#1089;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082; on 2009-06-28
Shockwave is a Windows only plugin that relies on Windows only resources. You will need to use Wine to install Windows version of Shockwave under the Linux version of Firefox. An excelent tutorial is here: [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

### Post by m_ad on 2009-06-28
> **&#1082 said:**
> Shockwave is a Windows only plugin that relies on Windows only resources. You will need to use Wine to install Windows version of Shockwave under the Linux version of Firefox. An excelent tutorial is here: [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

thanks for the response, but did you read my original post, or just the title? :popcorn:


> **m_ad said:**
> I followed the directions on [this]("https://help.ubuntu.com/community/Shockwave") page, and I _thought_ I had a working version of shockwave for firefox under windows. When I tried to use mozplugger and attempt to test the shockwave player, I just get a blank page.

I know I'm not explaining this well, but firefox isn't telling me it needs a plugin. Instead, it's just a blank page.

---

### Post by &#1082;&#1086;&#1084;&#1084;&#1091;&#1085;&#1080;&#1089;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082; on 2009-06-28
> **m_ad said:**
> thanks for the response, but did you read my original post, or just the title? :popcorn:
I'm sorry, I wasn't aware of the link. It blends in with the rest of the text on my computer. Would you post the contents of the page [noparse]"about:plugins"[/noparse] ?

---

### Post by m_ad on 2009-06-28
thanks :)


```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
VLC Multimedia Plugin (compatible Totem 2.26.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/vlc 	VLC Multimedia Plugin 		Yes
video/x-google-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	Annodex exchange format 	anx 	Yes
audio/annodex 	Annodex Audio 	axa 	Yes
video/annodex 	Annodex Video 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
MozPlugger 1.12.0 handles QuickTime and Windows Media Player Plugin

    File name: mozplugger.so
    MozPlugger version 1.12.0, written by Fredrik Hübinette, Louis Bavoil and Peter Leese.
    For documentation on how to configure mozplugger, check the man page. (type man mozplugger)
    Configuration file:	/etc/mozpluggerrc
    Helper binary:	mozplugger-helper
    Controller binary:	mozplugger-controller
    Link launcher binary:	mozplugger-linker

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG animation 	mpeg,mpg,mpe 	Yes
video/x-mpeg 	MPEG animation 	mpeg,mpg,mpe 	Yes
video/x-mpeg2 	MPEG2 animation 	mpv2,mp2ve 	Yes
video/mp4 	MPEG4 animation 	mp4 	Yes
video/msvideo 	AVI animation 	avi 	Yes
video/x-msvideo 	AVI animation 	avi 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
application/x-mplayer2 	Windows Media video 	* 	Yes
video/x-ms-asf 	Windows Media video 	asf,asx 	Yes
video/x-ms-wm 	Windows Media video 	wm 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wvx 	Yes
video/x-ms-asf-plugin 	Window Media video 	* 	Yes
application/asx 	Windows Media video 	asx 	Yes
application/x-quicktimeplayer 	Quicktime animation 	mov 	Yes
image/x-macpaint 	Quicktime animation 	pntg,mov 	Yes
video/quicktime 	Quicktime animation 	mov,qt 	Yes
video/x-quicktime 	Quicktime animation 	mov,qt 	Yes
video/x-theora 	OGG stream with video 	ogg 	Yes
video/theora 	OGG stream with video 	ogg 	Yes
video/ogg 	OGG stream with video 	ogg 	Yes
video/x-ogg 	OGG stream with video 	ogm,ogv 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
audio/x-mp3 	MPEG audio 	mp3 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mpeg 	MPEG audio 	mpa,abs,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mpa,abs,mpega 	Yes
audio/x-ogg 	OGG audio 	ogg 	Yes
application/x-ogg 	OGG audio 	ogg 	Yes
application/ogg 	OGG audio 	ogg 	Yes
audio/x-ms-wax 	Windows Media Audio 	wax 	Yes
audio/x-ms-wma 	Windows Media Audio 	wma 	Yes
application/pdf 	PDF file 	pdf 	Yes
application/x-pdf 	PDF file 	pdf 	Yes
text/pdf 	PDF file 	pdf 	Yes
text/x-pdf 	PDF file 	pdf 	Yes
application/x-postscript 	PostScript file 	ps 	Yes
application/postscript 	PostScript file 	ps 	Yes
application/x-rtf 	Rich Text Format 	rtf 	Yes
application/rtf 	Rich Text Format 	rtf 	Yes
text/rtf 	Rich Text Format 	rtf 	Yes
application/x-msword 	Microsoft Word Document 	doc,dot 	Yes
application/msword 	Microsoft Word Document 	doc,dot 	Yes
application/vnd.ms-excel 	Microsoft Excel Document 	xls,xlb 	Yes
application/vnd.sun.xml.writer 	OpenOffice Writer 6.0 documents 	sxw 	Yes
application/so7_vnd.sun.xml.writer 	OpenOffice Writer 7.0 documents 	sxw 	Yes
application/vnd.sun.xml.writer.template 	OpenOffice Writer 6.0 templates 	stw 	Yes
application/vnd.sun.xml.writer.global 	OpenOffice Writer 6.0 global documents 	sxg 	Yes
application/vnd.stardivision.writer 	StarWriter 5.x documents 	sdw 	Yes
application/vnd.stardivision.writer-global 	StarWriter 5.x global documents 	sgl 	Yes
application/x-starwriter 	StarWriter 4.x documents 	sdw 	Yes
application/vnd.sun.xml.calc 	OpenOffice Calc 6.0 spreadsheets 	sxc 	Yes
application/so7_vnd.sun.xml.calc 	OpenOffice Calc 7.0 spreadsheets 	sxc 	Yes
application/vnd.sun.xml.calc.template 	OpenOffice Calc 6.0 templates 	stc 	Yes
application/vnd.stardivision.calc 	StarCalc 5.x spreadsheets 	sdc 	Yes
application/x-starcalc 	StarCalc 4.x spreadsheets 	sdc 	Yes
application/vnd.lotus-1-2-3 	Lotus 1-2-3 Document 	123, wk1 	Yes
application/vnd.sun.xml.draw 	OpenOffice Draw 6.0 documents 	sxd 	Yes
application/so7_vnd.sun.xml.draw 	StarOffice Draw 7.0 documents 	sxc 	Yes
application/vnd.sun.xml.draw.template 	OpenOffice Draw 6.0 templates 	std 	Yes
application/vnd.stardivision.draw 	StarDraw 5.x documents 	sda 	Yes
application/x-stardraw 	StarDraw 4.x documents 	sda 	Yes
application/vnd.sun.xml.impress 	OpenOffice Impress 6.0 presentations 	sxi 	Yes
application/so7_vnd.sun.xml.impress 	StarOffice 7.0 Impress presentations 	sxi 	Yes
application/vnd.sun.xml.impress.template 	OpenOffice Impress 6.0 templates 	sti 	Yes
application/vnd.stardivision.impress 	StarImpress 5.x presentations 	sdd 	Yes
application/vnd.stardivision.impress-packed 	StarImpress Packed 5.x files 	sdp 	Yes
application/x-starimpress 	StarImpress 4.x presentations 	sdd 	Yes
application/vnd.ms-powerpoint 	PowerPoint Slideshow 	ppt 	Yes
application/mspowerpoint 	PowerPoint Slideshow 	ppt,ppz,pps,pot 	Yes
application/vnd.sun.xml.math 	OpenOffice Math 6.0 documents 	sxm 	Yes
application/so7_vnd.sun.xml.math 	StarOffice 7.0 Math documents 	sxm 	Yes
application/vnd.stardivision.math 	StarMath 5.x documents 	smf 	Yes
application/x-starmath 	StarMath 4.x documents 	smf 	Yes
application/vnd.oasis.opendocument.text 	OASIS OpenDocument Text 	odt,ODT 	Yes
application/vnd.oasis.opendocument.spreadsheet 	OASIS OpenDocument SpreadSheet 	ods,ODS 	Yes
application/vnd.oasis.opendocument.presentation 	OASIS OpenDocument Presentation 	odp,ODP 	Yes
application/x-director 	Macromedia Director file 	dir,dcr,dxr,cst,cct,cxt,w3d,fgd,swa 	Yes

```

---

