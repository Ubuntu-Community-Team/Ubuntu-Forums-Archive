---
title: "install nvidia graphics driver manually"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by bobin on 2009-04-24
how do i do that ? i got intrepid

---

### Post by jowilkin on 2009-04-24
It's generally not a good idea to install manually unless you really need the newest driver for some reason.  If you install manually you will need to reinstall every time you upgrade your kernel.  It can also be troublesome to uninstall or upgrade a manually installed driver.

If you do really need the newest driver then you can get it from Nvidia's website: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Select the one for your architecture and save it to your hard drive.

Then you need to exit the X server.  You can do this by pressing Control-Alt-F1 which should bring you to a command prompt.  Then stop the x server with the command "sudo /etc/init.d/gdm stop".

Once that's done, just navigate to the directory you saved the driver in and run it with "sudo sh driver_file_name" where you substitute the name of the file into the command.

---

### Post by inobe on 2009-04-24
> **bobin said:**
> how do i do that ? i got intrepid

please explain why you want to manually install a video driver ?

is there something wrong with your video, if so tell us about your video card' the make and model and include the trouble you are experiencing.

---

### Post by jowilkin on 2009-04-24
I can't speak for the original poster, but I had to manually install because HDMI on my card would not work without a newer driver than was available in the repos.  So there are instances when it's required.

---

### Post by inobe on 2009-04-24
include the hardware information and maybe we can provide an easier alternative.

---

### Post by jowilkin on 2009-04-24
If you are referring to me, I have an Asus P5N7A-VM motherboard with onboard video and I'm using the HDMI out to output sound and video to my plasma tv.  Chipsets on the board are NVIDIA GeForce 9300/nForce 730i.

Only way I could get this working (in 8.10) was to manually upgrade to the latest nvidia drivers and alsa.  It also required further tweaking in alsamixer (unmuting some channels that were muted by default for some reason).

I'm installing Jaunty right now and will attempt to get it working using aptitude before resorting to manual installs.

---

### Post by inobe on 2009-04-24
i am glad you told me this, i can tell you how to get the very latest on each stable nvidia release.

first go here and add the source to synaptic

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

thanks to the fella that owns and maintains this site.

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

check post #716

[http://ubuntuforums.org/showthread.php?t=990978&page=72](http://ubuntuforums.org/showthread.php?t=990978&page=72)

i am running the current 180.51 with that source.

---

### Post by jowilkin on 2009-04-24
No audio on jaunty.  I'm guessing the nvidia driver is new enough since they have the 180 series, but alsa is too old.

I'm now using this ppa: [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa), it also seems to have the latest nvidia drivers.  I use xbmc as my media player and the latest xbmc lists this ppa as a dependency (i think to make sure you have the latest nvidia drivers).  It has nvidia 185.19 which I believe is beta but has better support for VDPAU.  Thanks for your suggestion also.

Any idea how to get alsa through repos?  Best method I've found is the script in this thread: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Edit: nevermind, I think I got the sound by unmuting the IEC958 channels in alsamixer and then going to Preferences -> sound on the gnome menu and changing all the options from autodetect to "HDA NVidia HDMI (ALSA)".  Looks like jaunty has new enough nvidia and alsa for my setup.

---

### Post by inobe on 2009-04-24
> **jowilkin said:**
> but alsa is too old.

Any idea how to get alsa through repos?/showthread.php?p=6589810[/url]

not certain but will look around.

---

### Post by jowilkin on 2009-04-24
I might have spoken too soon about audio working properly.  It seems that *some* audio works and some doesn't.

---

### Post by inobe on 2009-04-24
the audio levels can be tricky if you are uncertain which does what.

---

### Post by jowilkin on 2009-04-24
> **inobe said:**
> the audio levels can be tricky if you are uncertain which does what.

I'm pretty sure I have the same config that was working under 8.10, aside from installing the newest alsa manually.  So if I can't get it working with a little more mucking around I will resort to a manual alsa install.

---

### Post by jowilkin on 2009-04-26
Well even with a manual install of a more recent Alsa I still couldn't get sound through HDMI working 100% again in jaunty.  I just went back to using a discrete sound card instead of the built in card and not using HDMI for sound :(

It's not making a quality difference, but was nice to have just the 1 wire.  I will just have to wait until HDMI support improves.

---

### Post by inobe on 2009-04-26
> **jowilkin said:**
> Well even with a manual install of a more recent Alsa I still couldn't get sound through HDMI working 100% again in jaunty.  I just went back to using a discrete sound card instead of the built in card and not using HDMI for sound :(

It's not making a quality difference, but was nice to have just the 1 wire.  I will just have to wait until HDMI support improves.

i seen many articles around here jowilkin.

---

### Post by jowilkin on 2009-04-26
I've been through tons of articles myself and after a lot of effort got it working in Intrepid.  I don't have the patience to do it again.  It's a real pain to get it right.  It seems that no two people get it working with the same strategy, it's hit and miss.

I imagine within a couple years support will improve greatly so I'm fine with waiting until that happens and using my 100% working setup for now.

---

