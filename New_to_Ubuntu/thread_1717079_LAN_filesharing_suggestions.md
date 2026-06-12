---
title: "LAN filesharing suggestions"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by notidaho on 2011-03-29
So I'm about to move in with 2 mates and we want to network out Xp/Vista/Win7 PCs in order to file share and play media in the lounge on a TV.

I have an not-to-old 40Gb, 2000MHz PC with integrated graphics and the latest Ubuntu (server and desktop) CDs at hand.

Can anyone advise me on the ideal setup for my requirements.

I presume the need to TV-out means I can't use the server and I'm aware I can install file-sharing mods to Ubuntu desktop. 

I read it's simple to TV-out from Linux but I've only ever done it on Windows. Can Linux even play .avi and mp3?

I could just setup a Windows network here but I really want to get some exererience in with Linux and servers (I also do a little webdesign), so any well informed tips would be greatly appreciated.

Cheers, Ian

---

### Post by mcduck on 2011-03-29
So the server is going to be the machine sitting next to the TV?

I'd probably use [XBMC]("http://xbmc.org/") for the media playing capabilities, and add a Samba server for sharing the files to the other Windows computers.

(both XBMC and Samba should be available from Ubuntu's repositories)

And yes, Linux can definitely play AVI files and MP3 audio. :D Although keep in mind that AVI is not a video format, it's a *container* and can contain video and audio encoded in pretty much any format. So there's no specific codec for AVI, you need to have the codecs for the actual video format used in the file to play it back. Installing all available gstreamer codec packages and the w32codecs package should give you support for all commonly used formats.

---

### Post by Tmcarr on 2011-03-29
Ok, heres what I'm doing. 

I have a western digital live plus player( [Its here on Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136593&Tpk=Western%20Digital%20Live%20plus"), $100, total STEAL). It has gigabit ethernet, HDMI out, Optical out.

Then, I use b-rad's WDLXTV([http://b-rad.cc/](http://b-rad.cc/)) firmware and ssh into it to setup sshfs shares over my local lan. 

ITs slightly lacking, and XBMC is certainly more flexible, but you wont find anything better for that cheap.

---

### Post by notidaho on 2011-03-29
Thanks guys I'll look in to both of those options. You're right in presuming I intend to have a networked PC next to my TV. I'm not familiar with Samba or SHH, will the files be accessed over the network or moved in to a shared folder on the server? 40Gbs isn't ideal for mass storage.

I currently have Ubuntu server installed but I presume I need graphical interface if I'm gonna have a media centre and potentially install codecs and the like.

TmCarr surely if XBMC is more flexible it's better because it's free and you don't need extra hardware? I suppose I'd have to get a usb device anyway if I get a remote anyway. I've heard of remotes for WMP, can you get them for other media centres? I'm so tired of using my feet to skip credits and it's gonna come in handy.

We will actually have an X-box 360, which I'm aware you can connect to PC, but presume it can't be networked like I want.

If the media centres installed on Ubuntu, what's the connection to the TV? I'm currently dual screening my Windows desktop with S-Video cables and Radeon card, but my server will have integrated graphics and Linux GUI.

---

### Post by mcduck on 2011-03-29
Samba is for Windows file sharing, just like you'd do between Windows computers. (it uses the SMB protocol Windows uses for file sharing). If you are going to keep the files on Windows computers, then you don't even need the Samba server. The client is included in Ubuntu by default so you can access your Windows shares without any extra software.

Another option would be running any uPNP media server on the Windows machines, if I remember right XBMC can connect to those as well. Although you'd probably get most out of it's library support if you had the files on the XBMC machine or on a normal network share.

XBMC supports remote controllers. Even better, if you happen to have Android phone there's an free Android app for controlling it. Probably the coolest remote controller one could think of, as it allows not only normal remote functions but also browsing content and viewing all information etc. directly on the remote... ;)

What comes to TV connection, that pretty much depends on what connectors are available on your computer & TV.

---

