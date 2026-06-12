---
title: "Does ubuntu have any software that..."
date: 2009-09-05
forum: New to Ubuntu
---

### Post by jeffski on 2009-09-05
Similar to BID (Bulk Image Downloader), this will download images, in bulk.

There is nothing that does what i need, now this is a family site so do be respectful of that in your assumptive responses.

Say there is an image hosting site, that host images of textures, or kittens etc. Then i find a gallery that has loads of images that i wanted to keep. Normally i would have to open each link to save the images manually.

Yes there are some programs that will download all the linked images but not all sites just link to their images as they have advertising to think about. Commonly the thumbnails will be linked to another page that has the full image, surrounded by adverts. This makes all these programs pretty useless.

This is what i want the program to do
```
read the html, list all links that match http://www.imagehostingsite.com/image.php?*,
read linked pages, list all images on linked pages, download all images over 57Kb
```I just wish i knew how to do perl or C+ or whatever it is programmers use.

If there is currently any programs that do this (for linux), then they are very hard to find.

---

### Post by Xenomorph05 on 2009-09-05
To save you from installing a new program if you use FireFox then get the Download helper add-on.

---

### Post by ks07 on 2009-09-05
> **Xenomorph05 said:**
> To save you from installing a new program if you use FireFox then get the Download helper add-on.
A similar suggestion from me, a good Firefox add-on that may be able to help you is "DownThemAll!". I know it can list and download all of a certain file type, but it may have more advanced settings that I have never bothered with myself. Give it a go, I hope it does the trick. :)

---

### Post by scragar on 2009-09-05
If you could provide an example of what your problem is I might be able to write something up in perl or bash.

---

### Post by Finalfantasykid on 2009-09-05
You might find what you want using wget

```
man wget
```

---

### Post by jeffski on 2009-09-05
> **scragar said:**
> If you could provide an example of what your problem is I might be able to write something up in perl or bash.

This would be awesome.

take this page for our example [LINK]("http://www.imagefap.com/gallery/1851131")

the thumbnails are links to pages, not direct links to images.

this means download helper and all the other suggested programs will not work. thank you all anyway for your suggestions.

i need a program that will check all the links, find any jpg/gif's larger than say 50Kb and save them to a folder.

---

### Post by jeffski on 2009-09-05
> **Finalfantasykid said:**
> You might find what you want using wget

```
man wget
```

```
wget -r -l1 --no-parent -A.jpg http://www.imagefap.com/gallery/1851131
```

like this? well that exact code doesn't work.

```
$ wget -r -l1 --no-parent -A.jpg http://www.imagefap.com/gallery/1851131
--2009-09-05 20:02:33--  http://www.imagefap.com/gallery/1851131
Resolving www.imagefap.com... 77.247.179.166, 77.247.179.157, 77.247.179.165
Connecting to www.imagefap.com|77.247.179.166|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `www.imagefap.com/gallery/1851131'

    [  <=>                                  ] 38,982       187K/s   in 0.2s    

2009-09-05 20:02:33 (187 KB/s) - `www.imagefap.com/gallery/1851131' saved [38982]

Removing www.imagefap.com/gallery/1851131 since it should be rejected.

FINISHED --2009-09-05 20:02:33--
Downloaded: 1 files, 38K in 0.2s (187 KB/s)

```

I think the answer is a simple bash or perl script. I'm googling how to write programs with perl now lets see if i can learn to write program before Christmas lol

---

### Post by sourav123 on 2009-09-05
> **scragar said:**
> If you could provide an example of what your problem is I might be able to write something up in perl or bash.

No need to reinvent the wheel. Use any of the below options:

1. Firefox add-on [e.g. Video Download Helper, DownThemAll etc.]
2. A command line based tool like wget or curl.

I prefer option 2 because it is really fast and flexible but finally it is up to individual user to decide.

---

### Post by Xenomorph05 on 2009-09-05
There is a BID firefox add-on but it seems to be Windows only since BID requires windows. This sounds like an awesome program. I had not heard of it before and great for downloading a lot of "kitten" pictures from thumbnail galleries.

It's too bad BID didn't work in WINE.

---

### Post by jeffski on 2009-09-05
> **sourav123 said:**
> No need to reinvent the wheel. Use any of the below options:

1. Firefox add-on [e.g. Video Download Helper, DownThemAll etc.]
2. A command line based tool like wget or curl.

I prefer option 2 because it is really fast and flexible but finally it is up to individual user to decide.


Well thank you but if you would like to add download helper (which i already use to teef youtube vids) then try it with this page [**LINK**]("http://www.imagefap.com/gallery/1851131") you will see why sometimes round wheels don't work!
I have tried every download manager/helper/automator that is available for linux. i have not yet found ONE that does what I need.

I have also tried to use wget (see my post above) this does not achive what i need, and is far too complicated anyway.

What i need is a program that:
1 - reads the web page
2 - reads the links on the said web page
3 - identifies any images that are over a certain size
4 - saves the said images to a location of my choice

the programs that you all kindly suggested will not do this. they will only download links, and this relys on the thumbnails to link directly to the picture. BUT as i said in my original post many image hosting sites (especially free ones) will have thumbs linked to pages, which contrain the images, surrounded by adverts.

sourav, if you could suggest a command that will do exactly what i have listed then please let me know since my attempt did not give me the results
wget -r -l1 --no-parent -A.jpg [http://www.imagefap.com/gallery/1851131](http://www.imagefap.com/gallery/1851131)
. please use the [LINK]("http://www.imagefap.com/gallery/1851131") as an example. imagefap has thumbnailed galleries which link to pages with the image on that, perfect example.

---

### Post by jeffski on 2009-09-05
i am trying to learn programming because all you programmers are too busy programming things to help little old me :(
```

#!/usr/bin/perl

open(gallery, '<', "http://www.imagefap.com/gallery/1851131") or die $!;

```

does this open the web page? oh it took me hours to learn this much and i havent learned how to test it yet.
if it does open the page then yay, how can i get it to then print anything that has "HREF" html tag?

i am trying to understand all this but it is starting to get too much for tonight, please help me somebody please :)

---

### Post by scragar on 2009-09-06
This took a while to write, so I hope you appreciate it:
```
#!/usr/bin/perl

use LWP::Simple;

use constant GALLERYURL	=> "http://www.imagefap.com/gallery.php?gid=";
use constant IMAGEURL	=> "http://www.imagefap.com/image.php?id=";

while(<STDIN>){
  chomp;
  /(\d+)/;

  print "Looking for gallery ID: $1\n";

  $url = GALLERYURL."$1&page=";
  $page = 0;
  do{
    $downloaded = 0;
    print "Downloading gallery listings for page ".($page+1)."\n";
    $_ = get $url.$page;
    print "Downloaded.\nGetting images from page.";
    while(/image\.php\?id=(\d+)&/g){
      $imagePage = get IMAGEURL.$1;

      $imagePage =~ m/lD\('(.*)'\)/;

      print "\nDecoding $1\n...\n";
      $imgUrl = lD($1);
      print $imgUrl . "\n\n";
      $downloaded++ if(system('wget', $imgUrl));
    }
    $page++;
  }while($downloaded > 0);

  print "No images on page.\nGallery download complete.\n\n";
}



BEGIN{
  sub unescape {
    my($str) = splice(@_);
    $str =~ s/%(..)/chr(hex($1))/eg;
    return $str;
  }
  sub lD{
    my $s = shift;
    my $s1 = unescape(substr($s,0,-1));
    my $sl = length $s1;
    my $sx = substr($s,-1,1);
    my $t = '';
    my @letters = unpack("C*", $s);
    for(my $i=0; $i<$sl; $i++){
      $t .= sprintf('%%%02X', $letters[$i] - $sx );
    }
    return unescape($t);
  }
}
```I had to reverse engineer the lD function that the site uses, which was much harder than I expected.
Usage:
Just call the script and give it a text file with the URLs for galleries, like so:
```
**[color=red]$[/color]** ls
imgfd
url_list.txt
**[color=red]$[/color]** cat url_list.txt
http://www.imagefap.com/gallery/1851131
**[color=red]$[/color]** perl imgfd < url_list.txt
Looking for gallery ID: 1851131
Downloading gallery listings
Downloaded.
Getting images from page.Decoding lxxt>33gegli2mqekijet2gsq3mqekiw3jypp37=354:354:8<:75542ntk4
...
http://cache.imagefap.com/images/full/39/106/1064863110.jpg

--2009-09-06 06:21:08--  http://cache.imagefap.com/images/full/39/106/1064863110.jpg
Resolving cache.imagefap.com... 77.247.179.169
Connecting to cache.imagefap.com|77.247.179.169|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51242 (50K) [image/jpeg]
Saving to: `1064863110.jpg'

100%[======================================>] 51,242       312K/s   in 0.2s    

2009-09-06 06:21:08 (312 KB/s) - `1064863110.jpg' saved [51242/51242]

**.......**
```
Fixed.

---

### Post by super kim on 2009-09-06
> **scragar said:**
> This took a while to write, so I hope you appreciate it:


I do !!  lol thats an awesome :KSscript:KS, you should make it into a fire fox add on:popcorn:

---

### Post by jeffski on 2009-09-06
Thank you scragar, yes i really appreciate it it does the job wonderfully.

oh no... it only downloads the first 24 links. i think it's because the standard layout is 14 images per page, i think the url should be:
[http://www.imagefap.com/gallery.php?gid=1851131&view=2](http://www.imagefap.com/gallery.php?gid=1851131&view=2)
not
[http://www.imagefap.com/gallery/1851131](http://www.imagefap.com/gallery/1851131)
that way all the images are put on one page, i tried adding```

http://www.imagefap.com/gallery.php?pgid=&gid=1851131&page=0
http://www.imagefap.com/gallery.php?pgid=&gid=1851131&page=1
http://www.imagefap.com/gallery.php?pgid=&gid=1851131&page=2
```
to the url_list.txt but it just downloaded three copies of the images.

i am sorry i didn't specify the "&view=2" bit, is it possible to add it in? I stayed up all night last night reading web pages about how to do perl, and i can just about make a script that can read and print some text. I tried to understand your perl script but it is too much for me to understand right now.

i'm amazed at how much you put into it, but it is a good thing, puppies and what not :)

---

### Post by scragar on 2009-09-06
/me facepalms for not realising there was a single page download.

```

#!/usr/bin/perl

use LWP::Simple;

use constant GALLERYURL	=> "http://www.imagefap.com/gallery.php?view=2&gid=";
use constant IMAGEURL	=> "http://www.imagefap.com/image.php?id=";

while(<STDIN>){
  chomp;
  /(\d+)/;

  print "Looking for gallery ID: $1\n";

  $downloaded = 0;
  print "Downloading gallery listings.\n";
  $_ = get GALLERYURL.$1;
  print "Downloaded.\nGetting images from page.";
  while(/image\.php\?id=(\d+)&/g){
    $imagePage = get IMAGEURL.$1;

    $imagePage =~ m/lD\('(.*)'\)/;

    print "\nDecoding $1\n...\n";
    $imgUrl = lD($1);
    print $imgUrl . "\n\n";
    $downloaded++ if(system('wget', $imgUrl));
  }
  if($downloaded == 0){
    print STDOUT "No images in gallery. You should check this.\n\n";
  }else{
    print "Downloaded $downloaded images.";
  }
}



BEGIN{
  sub unescape {
    my($str) = splice(@_);
    $str =~ s/%(..)/chr(hex($1))/eg;
    return $str;
  }
  sub lD{
    my $s = shift;
    my $s1 = unescape(substr($s,0,-1));
    my $sl = length $s1;
    my $sx = substr($s,-1,1);
    my $t = '';
    my @letters = unpack("C*", $s);
    for(my $i=0; $i<$sl; $i++){
      $t .= sprintf('%%%02X', $letters[$i] - $sx );
    }
    return unescape($t);
  }
}

```

---

### Post by scragar on 2009-09-06
> **super kim said:**
> I do !!  lol thats an awesome :KSscript:KS, you should make it into a fire fox add on:popcorn:

You're free to do whatever you want with it you know, public domain and all that. :p

---

### Post by jeffski on 2009-09-06
YAY thats the ticket!

i tried changing
```

use constant GALLERYURL    => "http://www.imagefap.com/gallery.php?gid=";
```
to```

use constant GALLERYURL    => "http://www.imagefap.com/gallery.php?gid=&view=2";
```
Thats so cool, so cool

---

### Post by scragar on 2009-09-06
> **jeffski said:**
> YAY thats the ticket!

i tried changing
```

use constant GALLERYURL    => "http://www.imagefap.com/gallery.php?gid=";
```
to```

use constant GALLERYURL    => "http://www.imagefap.com/gallery.php?gid=&view=2";
```
Thats so cool, so cool

Put the view=2 part before the gid=, otherwise it won't work as you want:
```
use constant GALLERYURL    => "http://www.imagefap.com/gallery.php?view=2&gid=";
```
I add the gallery ID to the end of the string.

I should have fixed it in my past post anyway.

---

### Post by jeffski on 2009-09-06
yea scragar your past post was fixed, thats what was so cool :D<br>

---

### Post by hamzah2096 on 2009-09-25
Can someone tell me how to use this script?

---

### Post by scragar on 2009-09-25
I posted usage when I posted the first version of the script(That didn't work with multiple pages unfortunately).

EDIT: to clarify you save the script as **imgfd** in my example(standing for **im**a**g**e**f**ap **d**ownloader).

Next make a list of the URLs you're going to download from, in my example it's url_list.txt
```
[color=red]**$**[/color] *cat url_list.txt*
http://www.imagefap.com/gallery/1851131
```
Then just call the script:
```
[color=red]**$**[/color] *perl imgfd < url_list.txt*
Looking for gallery ID: 1851131
Downloading gallery listings
...
```
Alternatively you could pass in the URLs by hand:
```
[color=red]**$**[/color] [I]perl imgfd
http://www.imagefap.com/gallery/1851131[/I]
Looking for gallery ID: 1851131
Downloading gallery listings
....
```
Whatever works for you(ctrl+C to exit the script when it's done)

---

