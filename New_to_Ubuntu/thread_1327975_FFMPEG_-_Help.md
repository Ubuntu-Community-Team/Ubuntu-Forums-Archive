---
title: "FFMPEG - Help"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by raj_rahul26 on 2009-11-16
Hi Guys,
   
I am new to this forum, presently am working on FFMPEG. It&#8217;s basically an open source package used to playback different formats like wmv, mpg, mp3 etc. I am able to successfully play the video formats like .mpeg, .m2v in Linux on x 86 systems. I have few doubts regarding FFMPEG, so wanted to share this on forum. I am trying to build MPEG specific player means to say that it should play MPEG 1 video and MPEG 2 video files only. I would be grateful to you people if you can help me out to solve this problem.ThankYou. :P

---

### Post by Arup on 2009-11-16
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

Some useful threads for you.

---

### Post by 3rdalbum on 2009-11-16
Use the 'file' command or 'libmagic' library to check the file type, and if it is not MPEG, display an error message.

Or, let the user play whatever their FFMPEG supports (happiest solution)

---

### Post by raj_rahul26 on 2009-11-16
[SIZE=4]Thanks for the reply.This was not the expected answer.Let me explain to you people in detail.FFMPEG folder has libavcodec, libavformat, libavutil etc.Inside the libavcodec folder there is lot of source codes of many codecs like mpeg, wmv, aac etc.I don't need these codecs since I am not interested in playing wmv files,only interested in playing only mpeg files.In order to this what has to be done is my question to all you people.Thank You.
[/SIZE]

---

### Post by Arup on 2009-11-16
> **raj_rahul26 said:**
> [SIZE=4]Thanks for the reply.This was not the expected answer.Let me explain to you people in detail.FFMPEG folder has libavcodec, libavformat, libavutil etc.Inside the libavcodec folder there is lot of source codes of many codecs like mpeg, wmv, aac etc.I don't need these codecs since I am not interested in playing wmv files,only interested in playing only mpeg files.In order to this what has to be done is my question to all you people.Thank You.
[/SIZE]

Post this question at the FFMPEG thread and Fake Outdoorsman will provide you with a way to compile with only FFMPEG support leaving out the rest. It has to be done during ./configure process.

---

### Post by 3rdalbum on 2009-11-16
When you said that you wanted to build an MPEG-specific player, I thought you meant that you were coding a video player for an embedded product, that uses FFMPEG as a backend.

I'm not sure why you want to remove all codecs except for a few. If you're so low on disk space that you need the extra room created by recompiling FFMPEG with fewer features, then perhaps Ubuntu is too heavy a distro for you.

---

### Post by raj_rahul26 on 2009-11-16
[SIZE=4]I thank Arup for his reply.If you don't mind can you please tell me FFMPEG thread name.Is this the thread which you meant to say: [http://ffmpeg.org/contact.html](http://ffmpeg.org/contact.html) Thank You.[/SIZE]:KS

---

### Post by raj_rahul26 on 2009-11-16
[SIZE=4]To 3rdAlbum,

    Thanks for your reply.I like to play only mpeg related video files but not wmv files etc. I want to remove unwanted source codes.So can you please suggest me an idea.:D

Thank You[/SIZE]

---

### Post by FakeOutdoorsman on 2009-11-16
Follow this guide:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

For step 2, use these dependencies instead:
```
sudo apt-get install build-essential subversion checkinstall texi2html libsdl1.2-dev
```

Skip step 3.  For the configure line on step 4, you can use something like this:
```
./configure --disable-encoders --disable-decoders --enable-decoder=mpeg1video --enable-decoder=mpeg2video --enable-decoder=mpegvideo
```
This example only enables MPEG-1 and 2 video as you requested.  There are many other *--disable-** options that you can use.  This is just a small example.  You can see more with *./configure --help*.  If you want to see what other decoders you can enable, use *./configure --list-decoders*.

Your font is big.

---

### Post by Arup on 2009-11-16
raj_rahul,

Fake Outdoorsman's guide is what we use here generally and you can see he has been kind enough to reply on this thread, I was referring to his guide as a matter of fact.

[http://www.tuxradar.com/content/code-project-create-ffmpeg-front-end](http://www.tuxradar.com/content/code-project-create-ffmpeg-front-end)

You might also be interested in this project here, take a look.

---

### Post by raj_rahul26 on 2009-11-24
Hi Guys,
               
           Thanks for the reply. Well, I want to share my work regarding FFMPEG & SDL to this forum. I am successful in installing and building FFMPEG on Windows (using MinGW & MSYS) and Fedora Core 3 .Since, I am interacting with you guys in Ubuntu forums, I wanted to do the same in Ubuntu and was successful in doing it with some minor changes in the install and build procedure.

              I am attaching the procedure to play the video file in Ubuntu:
  
1. SDL &#8211; Simple DirectMedia Layer
  Extract SDL-1.2.14.tar.gz. Under terminal, go to root directory SDL-1.2.14 and run following commands to install SDL:
  a)  ./configure 
b) make 
c) make install
  
2. FFMPEG
  Go to root directory and run following commands to build FFplay:
  a) ./configure 
              Before running make, read the configuration output and make sure that the SDL check is &#8220;yes&#8221;. This means you have correctly installed SDL libraries. Otherwise FFplay won&#8217;t be built.
  b) make
  c) make install
  
   If everything goes right, now you should be able to run ffplay.
  
3. Use FFplay
  Assume that you have m2v bitstream or any other bitstream in the same directory and run following command to play the file: ffplay videofilename.mpg
   
  My question to this forum is same as before with the help of ffplay, I want to play only mpeg2video files. I would like to remove all the .c and .h source codes which are not relevant in the FFMPEG package. I expect with the procedure I followed ffplay should be able to play only mpeg2video files. Thank you. :KS

---

### Post by 3rdalbum on 2009-11-24
> **raj_rahul26 said:**
> My question to this forum is same as before with the help of ffplay, I want to play only mpeg2video files. I would like to remove all the .c and .h source codes which are not relevant in the FFMPEG package. I expect with the procedure I followed ffplay should be able to play only mpeg2video files. Thank you. :KS

For what purpose? When you compile ffmpeg in the way described, the compiled binaries will not contain support for any other video formats. It doesn't matter what the source code contains - if the program has been compiled without a particular feature, then that feature is simply not included in ffmpeg.

After compiling, you can remove the source code from your hard disk.

---

### Post by raj_rahul26 on 2009-11-24
Hi 3rd Album,

    Thanks for the reply. I am doing the project where with the help of FFMPEG package I would like to do MPEG-2 specific video player.To the best of my knowledge if I compile the FFMPEG package .o(Object) files will be generated for the respective formats/codecs, this would be helpful in playing the video file.I didn't get you what you said about compiled binaries and which way are you intending to say to me. Thank You. :p

---

