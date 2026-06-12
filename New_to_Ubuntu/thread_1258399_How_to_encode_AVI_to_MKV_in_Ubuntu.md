---
title: "How to encode AVI to MKV in Ubuntu ?"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-09-05
I tried using HandBrake. I gave the input as AVI and Output container as MKV. I added it to the queue. Once I start encoding, handbrake closes itself. :(

How to solve the problem ? Doesn't Handbrake support converting from AVI to MKV ? What are the alternative tools to use ?

Please provide step by step guide for the software you recommend. I am really new to video encoding in Ubuntu. :confused:

---

### Post by defacto on 2009-09-05
You can try mencoder ( [Mediabuntu ]("https://help.ubuntu.com/community/Medibuntu")):
```
mencoder file.avi -ovc -oac -o output.mkv

```

---

### Post by andrew.46 on 2009-09-05
Hi SriLankanBoy,

> **SriLankanBoy said:**
>  What are the alternative tools to use ?

A very easy too to use for this purpose is the gui for mkvtoolnix:

```
sudo apt-get install mkvtoolnix-gui
```

It has a drag and drop interface and if you simply use the defaults you should still get a great result.

Andrew

---

### Post by lovinglinux on 2009-09-05
> **andrew.46 said:**
> Hi SriLankanBoy,



A very easy too to use for this purpose is the gui for mkvtoolnix:

```
sudo apt-get install mkvtoolnix-gui
```

It has a drag and drop interface and if you simply use the defaults you should still get a great result.

Andrew

+1 for mkvtoolnix

Keep in mind that AVI and MKV are just containers, so there is no need to encode from one format to the other, which would be a slow process.

With mkvtoolnix you simply mux audio, video and subtitle streams from AVI or other containers into the MKV container. So the process is very fast, without quality loss or significant size change.

---

### Post by SriLankanBoy on 2009-09-05
> +1 for mkvtoolnix

Keep in mind that AVI and MKV are just containers, so there is no need to encode from one format to the other, which would be a slow process.

With mkvtoolnix you simply mux audio, video and subtitle streams from AVI or other containers into the MKV container. So the process is very fast, without quality loss or significant size change.

I got some TV Shows with size of 350MB . So the entire season does not fit under a standard 4.7GB DVD. Therefore I want to encode the 350MB AVI into a 175MB MKV . I have heard that this process could bring a great output within the specified size. :)

EDIT : How to specify the output size in mkvtoolnix ? :confused:

---

### Post by lovinglinux on 2009-09-05
> **SriLankanBoy said:**
> EDIT : How to specify the output size in mkvtoolnix ? :confused:

You can't. As I said, [MKV](http://en.wikipedia.org/wiki/Matroska) is not a codec, is just a container, and mkvtoolnix is not an encoder, is just a muxer. All it does is "mix" whatever audio, video and subtitle tracks you specify from different sources into a single MKV container.

> **SriLankanBoy said:**
> I got some TV Shows with size of 350MB . So the entire season does not fit under a standard 4.7GB DVD. Therefore I want to encode the 350MB AVI into a 175MB MKV . I have heard that this process could bring a great output within the specified size. :)

MKV is popular format for TV shows and movies because it can combine several audio tracks and subtitles into a single file, which AVI cannot, besides being an open format and compatible with DVD players and media center extenders. The size and quality of the video has nothing to do with the format, but with the codecs used to encode the video. The codec used to encode video in mkv files is usually [h.264](http://en.wikipedia.org/wiki/H.264), which is also the one used by mp4 files.

So what you are looking for is an application that can transcode video using h.264 codec. You can do that with graphical interfaces like Avidemux, WinFF and Handbrake or using a command-line tool like mencoder or ffmpeg. Depending on the software you choose, you will have to transcode the video to mp4 format, using h.264 codec and then muxing it into an mkv file with mkvtoolnix. But I believe the only reason you want to use mkv is because of size of the file and quality of the video, so encoding it to mp4 would have the same effect, without the "hassle" (actually is pretty easy) of muxing it to an mkv container .

Keep in mind that h.264 is not a miracle maker. I have seen some really good encoded videos in the 175 Mb range, but they are rare. The thing is that if you want high-quality video with that size, you have to tweak the encoder settings a lot and probably encode the video with several passes, to maximize the quality while keeping the size small. Don't expect to much if you just click the "convert button" without configuring the encoder and waiting several hours to transcode the video.

If you find a good configuration to do that, specially with mencoder, please let me know. I'm currently improving the PVR feature of my media center extension for Firefox, which currently uses 900 Mb/h to 5Gb/h of recorded video, depending on the quality settings.

---

### Post by andrew.46 on 2009-09-06
Hi SriLankanBoy,

> **SriLankanBoy said:**
> How to specify the output size in mkvtoolnix ? :confused:

As lovinglinux has pointed out mkvtoolnix will not *shrink* a media file as such. Many are not aware that mkvtoolnix can *split* bigger files up in several different ways. Unfortunately not much use in your scenario but perhaps something to keep in mind for later? I attach a screenshot showing the menu I am referring to.

Andrew

---

