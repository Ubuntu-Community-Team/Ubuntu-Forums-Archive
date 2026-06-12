---
title: "download torrents from rss feed"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-09-13
I currently use transmission to download torrents. It works fine but does not have any rss feed integration. I have tried various other torrent clients, including deluge and vuze, but have found the rss feed plugins too complicated for my simple needs. Basically, I have configured a feed with shows I want to download. All the client has to do is update the feed every few minutes and download all the torrent. I don't need complicated filters or any limits or anything like that. Does such a thing exist?

---

### Post by ankspo71 on 2009-09-13
Hi,

If you are downloading podcasts (audio/video) try "Miro". It can be found in Synaptic Package Manager or:
```
sudo apt-get install miro
```
in your terminal, and even on the web.

---

### Post by abhiroopb on 2009-09-13
Thanks but I actually use that already. Was looking for something for torrents.

---

### Post by ankspo71 on 2009-09-14
I was checking out Ktorrent on the net, and according to this forum post, rss feeds are supported.
[http://ktorrent.org/forum/viewtopic.php?f=1&t=3176&hilit=rss](http://ktorrent.org/forum/viewtopic.php?f=1&t=3176&hilit=rss)

Btw, I can download any torrent through Miro (I just downloaded Ubuntu ISO to double check). I did it by copying and pasting the torrent URL in the menu. The only thing is, if you subscribe to an RSS torrent feed, it asks if it is a audio or video feed. So I'm not sure if it will display any non audio or video items in your feed... but it might. It doesn't have a blocklist though.

As for Ktorrent, I have used it before in Ubuntu. It's pretty good, and it has alot of features. I never tried out the RSS feature, or even knew it had one until now though. It will download and install though Synaptic.

---

### Post by abhiroopb on 2009-09-14
I don't mind using Ktorrent (although by the looks of it, it seems just as troublesome as Vuze and deluge), but could someone provide an easy to configure guide. Like I said all I need it to do is download ALL the torrents from a certain rss feed.

---

### Post by abhiroopb on 2009-09-14
I've found a good solution that will allow me to both use Transmission AND download torrents from an RSS feed.

Transmission has a "watch directory" function. So all I need to do is download torrents from the RSS feed into that "watched directory".

Now I'm not sure how to do this, so help on this matter would be appreciated.

BTW Miro worked great, but I decided I'd rather figure out a way of making transmission work as it is a much better client (IMHO).

---

### Post by ankspo71 on 2009-09-14
Hi,
Here is a guide for Ktorrent.

Scroll down to:
Mininova.org RSS/Autodownload and KTorrent on Ubuntu = Ultimate Torrent Setup

[http://sproif.com/2008/07/09/mininovaorg-rssautodownload-and-ktorrent-on-ubuntu-ultimate-torrent-setup/](http://sproif.com/2008/07/09/mininovaorg-rssautodownload-and-ktorrent-on-ubuntu-ultimate-torrent-setup/)

I'll see what else I can dig up.
james.

---

### Post by abhiroopb on 2009-09-14
Thanks a lot for that, very useful. But what do you think of my "simpler" solution?

---

### Post by ankspo71 on 2009-09-14
I don't know, I didn't actually see what you wrote... we were typing at the same time. lol

If you download the .torrent meta-files (whatever they are called) before transmission actually downloads what you want, doesn't that sort of ruin the automated process? :confused:

I think I have an idea. Look for a rss news aggregator(?) that will automatically download the attachments. In this case it would be the .torrent meta-files.

---

### Post by abhiroopb on 2009-09-14
Yea that is the kind of thing that I had in mind. The automated process would be some sort of script or program that runs in the background and downloads all the .torrent metafiles into one folder and then transmission watches that directory and then download from that folder.

---

### Post by sunchiqua on 2009-09-14
Is it possible for you to share the feed URL with others ( it would be easier to understand, what exactly you need ) ?

---

### Post by abhiroopb on 2009-09-14
[http://showrss.karmorra.info/rss.php?user_id=1007](http://showrss.karmorra.info/rss.php?user_id=1007)

Thanks!

---

### Post by abhiroopb on 2009-09-14
Update of my feed:

[http://showrss.karmorra.info/rss.php?user_id=18150&hd=0&proper=0](http://showrss.karmorra.info/rss.php?user_id=18150&hd=0&proper=0)

---

### Post by abhiroopb on 2009-09-14
I think I have figured out the terminology. What I am looking to do is essentially "Broadcatching" ([http://en.wikipedia.org/wiki/Broadcatching](http://en.wikipedia.org/wiki/Broadcatching)).

There is a lot of information on it on the web, but other than the Java app TED there does not seem to be anything particular useful for Ubuntu. 

Ideally, I'd want a script that runs every 10-15 minutes and searches the specified feed for any new torrent files, and if there are any new torrent files it should download it to a folder which is then being scanned by Transmission (creating an autodownload function).

---

### Post by unutbu on 2009-09-14
abhiroopb, are you looking for a script to monitor a url web page, check for new torrents (differently named files?) and then issue a command based on the new files found?
If that is all it takes, I think I can write a script to do that.

Is this the page you want monitored:
[http://showrss.karmorra.info/rss.php?user_id=18150&hd=0&proper=0](http://showrss.karmorra.info/rss.php?user_id=18150&hd=0&proper=0)

and what is the command you'd like issued based on the new feeds found?

---

### Post by abhiroopb on 2009-09-14
Thats essentially it, unutbu.

Basically, I have configured that particular website to create a personalised RSS feed for me to only provide me with the torrents I require. So, every single torrent that shows up in that feed would have to be downloaded to my specially assigned "torrents" folder that is being watched by Tranmission.

It seems simple enough, but I have no idea how to go about it.

Thanks a lot for your help.

---

### Post by unutbu on 2009-09-14
Okay, once I have the list of new torrents, such as 

[http://torrent.zoink.it/True.Blood.S02E12.HDTV.XviD-NoTV.%5Beztv%5D.torrent](http://torrent.zoink.it/True.Blood.S02E12.HDTV.XviD-NoTV.%5Beztv%5D.torrent)

What does one do with this? Do you download this file to your computer and put it in a certain directory? Which directory? (As this makes abundantly clear, I am a torrent noob...)

---

### Post by abhiroopb on 2009-09-14
Thats pretty much all you have to do, once it appears in the specific directory, as long as your torrent client is running it should automatically add it.

All I would need the script to do is this:

1. Search RSS feed every few minutes
2. Download NEW .torrent file (this is obviously important as I don't want the same .torrent file being downloaded over and over again).
3. Place newly downloaded .torrent file in specified directory.

Then transmission (my bittorrent client of choice would download the torrent after scanning the specified directory.

---

### Post by unutbu on 2009-09-14
I know you do not need such explicit directions abhiroopb, but I'm writing it this way just in case others find this useful...

[list]
[*] Install the python-beautifulsoup package
[*] Save this to ~/bin/tormon.py 

[php]
#!/usr/bin/env python

import urllib2,urlparse
from urllib2 import HTTPError,URLError
from BeautifulSoup import BeautifulSoup
import os
import optparse

__usage__='''
tormon.py -O ~/test/tormon -u "http://rss.feed"
'''

class Main(object):
    '''
    tormon checks an rss feed for new torrents. When it finds a new .torrent, to
    downloads it to a specified output directory, where (presumably) a monitoring
    torrent program will download the corresponding file.    
    '''
    def parse_options(self):
        usage = 'usage: %prog [options]'+__usage__
        parser = optparse.OptionParser(usage=usage)
        parser.add_option(
            '-O', '--output_dir', dest='output_dir', 
            help='directory into which new torrents are saved', 
            metavar='DIR')
        parser.add_option(
            '-f', '--filetype', dest='filetype',
            action='append',
            default=[],
            help='admissible file types', 
            metavar='TYPE')
        parser.add_option(
            '-d', '--downloaded_torrents', dest='downloaded_torrents',
            default=os.path.expanduser('~/.downloaded_torrents'),
            help='log of already downloaded torrents', 
            metavar='FILE')
        parser.add_option(
            '-e', '--error_log', dest='error_log',
            help='log of torrents tormon failed to download', 
            metavar='FILE')
        parser.add_option(
            '-b', '--batch', dest='batch',
            help='file containing list of rss feed urls', 
            metavar='FILE') 
        parser.add_option(
            '-u', '--url', dest='url',
            action='append',
            default=[],
            help='url of the rss feed', 
            metavar='URL')
        parser.add_option(
            '-m','--mark_all_downloaded', dest='mark_all_downloaded',
            action='store_true', 
            default=False,
            help="mark all torrents as already downloaded")
        parser.add_option(
            '-M','--match_by_filename', dest='match_by_filename',
            action='store_true', 
            default=False,
            help="recognize downloaded files by filename, not URL. Matching by URL is the default.")        
        (self.opt, args) = parser.parse_args()
        if self.opt.batch:
            for line in open(self.opt.batch,'r'):
                line=line.strip()
                if line and not line.startswith('#'):
                    self.opt.url.append(line)
        if not self.opt.output_dir:
            self.opt.output_dir=os.path.expanduser('~/Desktop')
        if not self.opt.filetype:
            self.opt.filetype=['.torrent']
        if not self.opt.error_log:
            self.opt.error_log=self.opt.downloaded_torrents+'.errors'
        try:
            os.makedirs(self.opt.output_dir)
        except OSError:
            if not os.path.exists(self.opt.output_dir):
                print('tormon failed to create directory %s'%self.opt.output_dir)
                exit(1)
    def load_list_of_already_downloaded_torrents(self):
        try:
            self.downloaded=open(self.opt.downloaded_torrents,'r').read().split()
        except IOError:
            self.downloaded=[]
        try:
            self.errors=open(self.opt.error_log,'r').read().split()
        except IOError:
            self.errors=[]
    def update_downloaded(self,url):
        self.downloaded.append(url)
        try:
            self.errors.remove(url)
        except ValueError:
            pass        
    def download_torrent(self,url):
        try:
            sock=urllib2.urlopen(url)
        except (HTTPError, URLError):
            # print('tormon failed to download %s'%url)
            if url not in self.errors:
                self.errors.append(url)
        else:
            filename=self.url2filename(url)
            target_file=os.path.join(self.opt.output_dir,filename)
            print('Downloading %s'%target_file)
            content=sock.read()
            sock.close()
            fh=open(target_file,'w')
            fh.write(content)
            fh.close()
            self.update_downloaded(url)
    def url2filename(self,url):
        return os.path.basename(urlparse.urlparse(url)[2])
    def has_been_downloaded(self,url):
        if self.opt.match_by_filename:
            filename=self.url2filename(url)
            return (filename in [self.url2filename(link) for link in self.downloaded])
        else:
            return (url in self.downloaded)
    def parse_rss_feed(self):
        for url in self.opt.url:
            print('RSS feed: %s'%url)
            try:
                sock=urllib2.urlopen(url)
            except (HTTPError, URLError):
                print('tormon failed to download %s'%url)
            else:
                content=sock.read()
                sock.close()
                soup=BeautifulSoup(content)
                links=([link.nextSibling for link in soup.findAll('link')]+
                       [link['href'] for link in soup.findAll('a')]+
                       [link['url'] for link in soup.findAll('media:content')])
                for link in links:
                    if (any([link.lower().endswith(ending)
                             for ending in self.opt.filetype])
                        and not self.has_been_downloaded(link)):
                        if self.opt.mark_all_downloaded:
                            print('Marking %s as downloaded'%link)
                            self.update_downloaded(link)
                        else:
                            self.download_torrent(link)
    def save_list_of_already_downloaded_torrents(self):
        fh=open(self.opt.downloaded_torrents, 'w')
        fh.write('\n'.join(self.downloaded))
        fh.close()
        fh=open(self.opt.error_log, 'w')
        fh.write('\n'.join(self.errors))
        fh.close()
    def __init__(self):
        self.parse_options()        
        self.load_list_of_already_downloaded_torrents()
        try:
            self.parse_rss_feed()
        except KeyboardInterrupt:
            pass
        finally:
            self.save_list_of_already_downloaded_torrents()
if __name__=='__main__':
    Main()
[/php]
[*] Make it executable:
```

chmod +x ~/bin/tormon.py
```

[*] Test it:
```

tormon.py -O /path/to/downloaded/dot/torrent/files -u "http://rss.feed"
```
Putting the url of the rss feed in quotes protects the url from being misinterpreted by the shell.
[list]
[*] /path/to/downloaded/dot/torrent/files should be the directory where you wish the .torrents to be saved. 
[*] If you omit the -O flag, the files will be placed in ~/Desktop.
[*] You should see a list of the torrents downloaded. 
[*] If you run the same command again, nothing should be downloaded unless a new torrent has been added to the rss feed.
[*] This command creates /path/to/downloaded/dot/torrent/files if it does not already exist.
[*] It will save a list of the urls of successfully downloaded torrents to ~/.downloaded_torrents.
[*] I tried to make the script general enough to be of use to other people too. If some else has a rss feed they wish to monitor, they can use the command
```

tormon.py -u "http://rss.feed"
```
[*] To monitor more than one rss feed, you can use the -u flag multiple times:
```

tormon.py -u "http://rss.feed1" -u "http://rss.feed2"
```
[*] ~/.downloaded_torrents is a plain text file. If you wish to download the same torrent again, just delete the url from this file. If you wish to "blacklist" a certain torrent, you can just add the url to this file.
[*] If you want to save the list of downloaded torrents to a different file, you can use the command
```

tormon.py -d /path/to/downloaded/torrents/file -u "http://rss.feed1"
```
[/list]
[*] If everything seems to be working properly, then set up the cron job: Run
```

crontab -e

```
A text editor (e.g. nano) will pop up.

Add this to the top of the file, changing USER to your username (e.g. abhiroopb)
```

PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/USER/bin
MAILTO=USER
```

Put this anywhere under the "PATH=..." line. 
```

*/15 * * * * tormon.py -u "http://rss.feed"
```
This will run the tormon.py command once every fifteen minutes.

Make sure there is at least one blank line at the end of the crontab file. (It's a quirk of the cron program.)
Save and exit the text editor. 

If you have a mail transfer agent (e.g. exim4) installed, then the MAILTO=USER line in the crontab will tell cron to send you the output of the command in a (local) email message.
You then get to see what torrents have been most recently downloaded.

[*] That's it. See if it works. I'll be expecting your bug reports. Enjoy! :)
[/list]

---

### Post by abhiroopb on 2009-09-14
Hi there.

WOW! That is amazing! Its perfect, and it means I don't have to be running a clunky java programme in the background all day long.

I really love what you can do with linux!

Thanks again, like I said this is exactly what I was looking for, and with the help of the linux community it took me less than a day to find it!

NB: I have PMed you about something else.

---

### Post by jackmetal on 2009-09-26
> **unutbu said:**
> I know you do not need such explicit directions abhiroopb, but I'm writing it this way just in case others find this useful...


Amazing!!!  unutbu, this is pretty close to what I've been looking for also..  :-)

I've been using TED (Torrent Episode Downloader) for a long time, but it doesn't support very many private trackers, so I've been trying to figure out some other way to do this..  Thanks a million..  I'm going to try this and see if I can get it to work with my private tracker.

---

### Post by isaidi on 2009-10-13
This is Great! Thanks unutbu! I have been looking for something that would do this. RSS File Downloaded, not sure why it was so difficult.

Automatic is the only thing i found, but it is for MAC only. [http://codingcurious.com/automatic/](http://codingcurious.com/automatic/)

I will try your script.

---

### Post by bigben1313 on 2009-10-27
This is exactly what I was looking for as well.  I am having one problem, though.  The script crashes if I try to pull torrent files for the Daily Show.  Could it be something with the torrent file name?

The terminal output is:

```
ben@Ben-EeePC ~ $ tormon.py -O /home/ben/Downloads/Torrents
Downloading /The.Daily.Show.2009.10.26.%28PDTV-FQM%29%5BVTV%5D.torrent
Traceback (most recent call last):
  File "/bin/tormon.py", line 81, in <module>
    Main()  
  File "/bin/tormon.py", line 78, in __init__
    self.parse_rss_feed()
  File "/bin/tormon.py", line 70, in parse_rss_feed
    self.download_torrent(torrent)
  File "/bin/tormon.py", line 57, in download_torrent
    except (HTTPError, URLError):
NameError: global name 'HTTPError' is not defined

```

The script works fine if I don't try and pull from the Daily Show.  Any suggestions?

---

### Post by unutbu on 2009-10-27
bigben1313, could you post the url of the rss feed you are monitoring?

---

### Post by damnandy on 2009-10-28
Thanks Unutbu!!! 

Lovely Script!...but one question.

How would I monitor many RSS feeds from this one script??


Thanks Again!!!!

---

### Post by isaidi on 2009-10-28
I believe you would execute it as many times as you have rss feeds to monitor.

Schedule a job to execute each rss feed..

the script only maintains a text file to exclude already downloaded torrents..
Not sure what would happen though if you download the same torrent from different rss feeds.. Haven't tried it

---

### Post by vinutux on 2009-10-28
Try miro ...

---

### Post by abhiroopb on 2009-10-28
Miro is VERY bloated in my opinion. This provides the simplest option of downloading feeds.

---

### Post by isaidi on 2009-10-28
> **vinutux said:**
> Try miro ...

but Miro is a completed integrated solution. All that is required here is to download the torrent files from the RSS feed.

---

### Post by damnandy on 2009-10-29
I do like that Miro is an all in one resource...but I prefer the lightweight RSS script. I have no use for Miro's other options...I have a media player that incorporates any internet audio i may need as well as most popular TV streams AND I can use it with a remote...and as for a BT client..very very limited compared to others.

Honestly other than the ease of the RSS downloader (which wouldnt handle ALL of my feeds), its a paperweight on my desktop.

Still wondering how to add multiple instances to that one script...



Thanks!!!

---

### Post by unutbu on 2009-10-29
damnandy, I've altered [the script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") so you can now specify multiple rss feeds:
```

tormon.py -u http://rss.feed1 -u http://rss.feed2
```

---

### Post by damnandy on 2009-10-29
Thanks for the edit!

Works great...but.



> **unutbu said:**
> bigben1313, could you post the url of the rss feed you are monitoring?

I got the same response from this url [http://www.ezrss.it/search/index.php?show_name=Bored+To+Death&show_name_exact=true&date=&quality=&release_group=&mode=rss](http://www.ezrss.it/search/index.php?show_name=Bored+To+Death&show_name_exact=true&date=&quality=&release_group=&mode=rss)

and this one [http://www.ezrss.it/search/index.php?show_name=Family+Guy&show_name_exact=true&date=&quality=&release_group=&mode=rss](http://www.ezrss.it/search/index.php?show_name=Family+Guy&show_name_exact=true&date=&quality=&release_group=&mode=rss)

but it went through a few others just fine.


EDIT it seems to be crashing after certain feeds have been used, im getting the torrents but then its crashing with the same output errors.

---

### Post by aktiwers on 2009-10-29
Subscripted to this thread, nice script Ubutbu.

---

### Post by unutbu on 2009-10-29
Below is the output I get when I run tormon on the two rss feeds you posted. There are some torrents that it failed to download, but it doesn't crash tormon. In each case I believe the torrent url is broken, so there is nothing tormon can do to fix this. 

Does your output look the same as the one posted below, or are you getting the error bigben1313 posted? I don't think you should be seeing that message if you have the newest version of the script, but if so, please post the full error message.

Note also that it is necessary to put the rss feed url in quotes ("...") to protect some special symbols (like &) from being eaten up (and misinterpreted) by the shell.
```

% tormon.py -O /tmp/tormon -u "http://www.ezrss.it/search/index.php?show_name=Bored+To+Death&show_name_exact=true&date=&quality=&release_group=&mode=rss" -u "http://www.ezrss.it/search/index.php?show_name=Family+Guy&show_name_exact=true&date=&quality=&release_group=&mode=rss"
RSS feed: http://www.ezrss.it/search/index.php?show_name=Bored+To+Death&show_name_exact=true&date=&quality=&release_group=&mode=rss
Downloading /tmp/tormon/Bored.to.Death.S01E06.HDTV.XviD-NoTV.[eztv].torrent
Downloading /tmp/tormon/Bored.to.Death.S01E05.HDTV.XviD-NoTV.[eztv].torrent
Downloading /tmp/tormon/Bored.to.Death.S01E04.HDTV.XviD-SYS.[eztv].torrent
Downloading /tmp/tormon/Bored.to.Death.S01E03.HDTV.XviD-NoTV.[eztv].torrent
tormon failed to download http://torrent.zoink.it/Bored.to.Death.S01E02.REPACK.HDTV.XviD-NoTV.[eztv].torrent
Downloading /tmp/tormon/Bored.to.Death.S01E02.HDTV.XviD-NoTV.[eztv].torrent
Downloading /tmp/tormon/Bored.to.Death.S01E01.HDTV.XviD-NoTV.[eztv].torrent
Downloading /tmp/tormon/Bored.To.Death.S01E02.READNFO.DVDSCR.XviD-FFNDVD.[eztv].torrent
Downloading /tmp/tormon/Bored.To.Death.S01E01.READNFO.DVDSCR.XviD-FFNDVD.[eztv].torrent
RSS feed: http://www.ezrss.it/search/index.php?show_name=Family+Guy&show_name_exact=true&date=&quality=&release_group=&mode=rss
Downloading /tmp/tormon/Family.Guy.S08E03.PDTV.XviD-2HD.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S08E02.Family.Goy.PDTV.XviD-FQM.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E16.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E15.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E14.PDTV.XviD-DOT.[eztv].torrent
tormon failed to download http://torrent.zoink.it/Family.Guy.7x13.(PDTV-LOL)[VTV].torrent
tormon failed to download http://torrent.zoink.it/Family.Guy.S07E12.420.PDTV.XviD-FQM.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E11.PDTV.XviD-LOL.[eztv].torrent
tormon failed to download http://torrent.zoink.it/Family.Guy.S07E10.PDTV.XviD-LOL.[eztv].torrent
tormon failed to download http://torrent.zoink.it/Family.Guy.S07E09.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E08.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E07.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E06.PROPER.REPACK.PDTV.XviD-XOR.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E06.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E05.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E04.PDTV.XviD-2HD.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E03.PDTV.XviD-LOL.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E02.READNFO.PDTV.XviD-SYS.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E01.REPACK.PDTV.XviD-ETACH.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S07E01.PDTV.XviD-ETACH.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S06E12.PROPER.PDTV.XviD-E7.[eztv].torrent
Downloading /tmp/tormon/Family.Guy.S06E12.PDTV.XviD-2HD.[eztv].torrent
```

---

### Post by damnandy on 2009-10-30
Unutbu...

I fixed that problem on my own with a line at the top of the script, just needed to handle the errors.

runs perfectly now with all of my feeds.


Still working on the ecron setting, didnt seem to run last night.

---

### Post by abhiroopb on 2009-10-30
Hi Unutbu,

Thanks for helping out with this script.

I'm having a problem with your updated script. Basically, I decided to add more than one feed to it when you enabled that option. So my script looks like this:

```

#!/bin/bash

cd /home/user/Computers/Bash/Torrent

./tormon.py \
-O /home/user/MyDownloads/Torrents/Files/ \
-d /home/user/MyDownloads/Torrents/Files/EZTV.txt \
-u "http://ezrss.it/search/index.php?show_name=dexter&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss" \
-u "http://ezrss.it/search/index.php?show_name=how+i+met+your+mother&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss" \
-u "http://ezrss.it/search/index.php?simple&show_name=caprica&mode=rss" \

```

The torrents are all downloaded fine. The problem I have is that the file that keeps track of the already downloaded files (i.e. -d /home/user/MyDownloads/Torrents/Files/EZTV.txt) only keeps track of the first line rss feed. So, all the shows from that feed are noted to have been downloaded but the other shows from the other two rss feeds re-download every time I launch the script.

So, my EZTV.txt file looks like this:

```

http://torrent.zoink.it/Dexter.S04E05.Dirty.Harry.HDTV.XviD-FQM.[eztv].torrent
http://torrent.zoink.it/Dexter.S04E04.HDTV.XviD-SYS.[eztv].torrent
http://torrent.zoink.it/Dexter.S04E03.HDTV.XviD-SYS.[eztv].torrent
http://torrent.zoink.it/Dexter.S04E02.Remains.to.Be.Seen.HDTV.XviD-FQM.[eztv].torrent
http://torrent.zoink.it/Dexter.S04E01.HDTV.XviD-NoTV.[eztv].torrent
http://torrent.zoink.it/Dexter.S04E01.PREAiR.HDTV.XviD-WOOT.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E12.HDTV.XviD-aAF.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E11.HDTV.XviD-aAF.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E10.HDTV.XviD-0TV.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E09.HDTV.XviD-0TV.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E08.HDTV.XviD-LOL.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E07.HDTV.XviD-LOL.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E06.HDTV.XviD-LOL.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E05.HDTV.XviD-0TV.[eztv].torrent
http://torrent.zoink.it/Dexter.3x04.(HDTV-0TV)[VTV].torrent
http://torrent.zoink.it/Dexter.S03E03.HDTV.XviD-NoTV.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E02.HDTV.XviD-0TV.[eztv].torrent
http://torrent.zoink.it/Dexter.S03E01.REAL.PROPER.HDTV.XviD-aAF.[eztv].torrent
http://torrent.zoink.it/Dexter.3x01.(HDTV-PROPER-CRiMSON)[VTV].torrent

```

What do you think I need to do?

Thanks.

---

### Post by bigben1313 on 2009-11-02
Ubuntu: Sorry for the late reply.  I just tried the RSS that was crashing the old script with the new script and it goes though fine.  The RSS Feed is:

[http://showrss.karmorra.info/rss.php?user_id=11311&hd=null&proper=null](http://showrss.karmorra.info/rss.php?user_id=11311&hd=null&proper=null)

I also found that when it was crashing, the downloaded episodes before the crash would not be written to the log, so they would get re-downloaded every time.  I don't know if the new script will act the same way if it hits that error since the RSS feed now works.

Thanks a ton for writing this.  It is a lot more efficient than using some bloated program like TED.  Combining this with showRSS and ezRSS is a very powerful combination.

---

### Post by abhiroopb on 2009-11-02
An luck with my problem?

---

### Post by note32 on 2009-11-02
use ktorrent its epic;)

---

### Post by abhiroopb on 2009-11-02
I find it bloated!

---

### Post by unutbu on 2009-11-02
abhiroopb, I haven't been able to reproduce [the problem you mention]("http://ubuntuforums.org/showpost.php?p=8202374&postcount=36"). (Isn't that always the way with programmers? :p ) Do you perchance have a cron job that runs tormon.py multiple times? Each tormon.py process tries to write to the same file, EZTV.txt. If you spawn 2 processes at the same time, then the one that finishes first writes to EZTV.txt, and the the second one **overwrites** EZTV.txt, wiping out all the stuff that the first process wrote. 

If this is your situation, then the easiest way to fix it is to make sure that only one tormon.py process is running at any given time, and use the -u flag to monitor multiple feeds.

---

### Post by unutbu on 2009-11-02
bigben1313, thanks for pointing out the crashing problem. The new script that I posted a few days ago fixes this problem. Now tormon will simply print out a warning like
```

tormon failed to download http://torrent.zoink.it/How.I.Met.Your.Mother.4x22.(HDTV-LOL)[VTV].torrent
```

and then continue. As long as tormon doesn't crash, the complete list of downloaded episodes (.torrent files) will be correcty written to the log. 

Let me know if you find any more rss feeds which crash tormon.

---

### Post by abhiroopb on 2009-11-02
Thanks for the response.

I tried running the following in a terminal:

```

./tormon.py -O /home/user/MyDownloads/Torrents/Files/ -d /home/user/MyDownloads/Torrents/Files/EZTV.txt -u "http://ezrss.it/search/index.php?show_name=dexter&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss" -u "http://ezrss.it/search/index.php?show_name=how+i+met+your+mother&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss"
```

And I got the following error:
[code]
RSS feed: http://ezrss.it/search/index.php?show_name=dexter&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
Downloading /home/user/MyDownloads/Torrents/Files/Dexter.S04E06.HDTV.XviD-SYS.[eztv].torrent
Traceback (most recent call last):
  File "./tormon.py", line 93, in <module>
    Main()  
  File "./tormon.py", line 90, in __init__
    self.parse_rss_feed() 
  File "./tormon.py", line 82, in parse_rss_feed
    self.download_torrent(torrent) 
  File "./tormon.py", line 60, in download_torrent
    fh=open(target_file,'w') 
IOError: [Errno 2] No such file or directory: u'/home/user/MyDownloads/Torrents/Files/Dexter.S04E06.HDTV.XviD-SYS.[eztv].torrent'
[\code]

And I'm definitely not running simultaneous cron jobs. In fact I was only running that individual bash script at the time.

---

### Post by unutbu on 2009-11-03
abhiroopb, I was able to reproduce this error by literally running the command you posted.
The problem, at least for me, was that tormon fails to create the directory /home/user/test/Torrents/Files. I, qua normal user, do not have permission to create /home/user.
Could this be the problem for you too?

I've edited [the script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19")
so tormon will post a clearer error message when it can not create the download directory. 

If my guess about the cause of the problem is not correct then it's back to the drawing board. Otherwise, hurray! Let me know either way.

---

### Post by abhiroopb on 2009-11-03
Thanks for the update. I figured out the problem. Basically, I was being a little stupid. I would stop the script before it completed and thats why the file wouldn't update. Permissions is not an issue for me.

I actually only posted three out of about 10 feeds. I ran all 10 feeds together and naturally it took some time to run the script. I would stop the script prematurely and this would cause the list not to update.

Anyway problem solved. Thank!

---

### Post by abhiroopb on 2009-11-03
Since you updated the script I have noticed that I am getting errors while downloading:

```

RSS feed: http://ezrss.it/search/index.php?show_name=dexter&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?simple&show_name=caprica&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=the+big+bang+theory&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=house&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=supernatural&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=californication&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=the+office&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=lost&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
ztormon failed to download http://torrent.zoink.it/Lost.4x12.Theres.No.Place.Like.Home.HDTV.XviD-FoV.[eztv].torrent
RSS feed: http://ezrss.it/search/index.php?show_name=24&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=two+and+a+half+men&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=apprentice+UK&date=&quality=&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=The+apprentice&show_name_exact=true&date=&quality=&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=criminal+minds&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
tormon failed to download http://torrent.zoink.it/Criminal.Minds.4x23.(HDTV-2HD)[VTV].torrent
RSS feed: http://ezrss.it/search/index.php?show_name=heroes&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=star+wars&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=true+blood&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=flashforward&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
RSS feed: http://ezrss.it/search/index.php?show_name=the+simpsons&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
tormon failed to download http://torrent.zoink.it/The.Simpsons.20x18.(HDTV-PROPER-0TV)[VTV].torrent
tormon failed to download http://torrent.zoink.it/The.Simpsons.S20E17.PROPER.HDTV.XviD-NoTV.[eztv].torrent
tormon failed to download http://torrent.zoink.it/The.Simpsons.S20E17.HDTV.XviD-0TV.[eztv].torrent
tormon failed to download http://torrent.zoink.it/The.Simpsons.S20E16.HDTV.XviD-0TV.[eztv].torrent
tormon failed to download http://torrent.zoink.it/The.Simpsons.S20E13.HDTV.XviD-LOL.[eztv].torrent
RSS feed: http://ezrss.it/search/index.php?show_name=how+i+met+your+mother&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss
tormon failed to download http://torrent.zoink.it/How.I.Met.Your.Mother.4x22.(HDTV-LOL)[VTV].torrent
RSS feed: http://ezrss.it/search/index.php?show_name=V+2009&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss

```

---

### Post by JBAlaska on 2009-11-03
Maybe this will be useful: ```
http://tvtrss.sourceforge.net/screenshot.php
```

I haven't tried it myself as I'm not a Drug dealer or terrorist....J/K xD

---

### Post by abhiroopb on 2009-11-03
Wow thats a really useful programme. Still I don't need anything that complicated. This simple python script does exactly what I need (albeit with some errors!).

---

### Post by unutbu on 2009-11-04
abhiroopb, I made a small change to [the script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") . Now when you abort the program with Ctrl-c, the script updates the log file's the list of downloaded torrents.

The errors you are seeing, such as
```

tormon failed to download http://torrent.zoink.it/Lost.4x12.Theres.No.Place.Like.Home.HDTV.XviD-FoV.[eztv].torrent

```
are all due to the rss feed listing broken links. I thought users might want to be alerted to this fact so they don't wonder why an episode is missing.

I could make tormon less verbose. Let me know if that's what you'd prefer.

---

### Post by abhiroopb on 2009-11-04
No no the listing is really useful as it enables (as you say) to keep track of files that are not being downloaded. Is it possible to keep track of which torrents fail to download? Basically, the script creates a log file listing all the torrents that failed? 

Also any ideas why it would fail?

Thanks!

---

### Post by abhiroopb on 2009-11-04
Thanks for the change to the script.

---

### Post by unutbu on 2009-11-04
Done. [tormon]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") now saves a list of all urls it fails to download. By default the error log file shares the same name as the download log file with ".errors" appended to the end.

So for example, if your download log file is called EZTV.txt, then the error log
will be called EZTV.txt.errors. 

You can change the location with the "-e" flag too.

When you see an error message like
```

tormon failed to download http://torrent.zoink.it/Lost.4x12.Theres.No.Place.Like.Home.HDTV.XviD-FoV.[eztv].torrent

```
try pointing your web browser at the url. I'm getting a "404 - Not Found" error.
This leads me to believe the rss feed / webpage has a broken link listed. There's nothing tormon can do (except warn you of the failure) because the .torrent file is simply missing.

---

### Post by abhiroopb on 2009-11-04
Getting the following error from the updated script:

```

$ sh EZTV.sh 
Traceback (most recent call last):
  File "./tormon.py", line 2, in <module>
    import feedparser 
ImportError: No module named feedparser

```

Thanks for the update.

---

### Post by KillaB7 on 2009-11-04
Beautiful work, unutbu!

Just downloaded your latest work and am having a problem with the & symbol.
Working great with feeds in the following format: [http://showrss.karmorra.info/rss.php?user_id=xxxx](http://showrss.karmorra.info/rss.php?user_id=xxxx)

```

jack@e6400:~/Torrents$ tormon.py -O /home/jack/Torrents/ -u http://www.ezrss.it/search/index.php?show_name=Smallville&quality=720P&mode=rss
[1] 8382
[2] 8383
jack@e6400:~/Torrents$ RSS feed: http://www.ezrss.it/search/index.php?show_name=Smallville

```

---

### Post by abhiroopb on 2009-11-04
Put the URL in quotes "example.com"

UPDATE: fixed my problem. Just had to install the package python-feedparser.

---

### Post by KillaB7 on 2009-11-04
> **abhiroopb said:**
> Put the URL in quotes "example.com"

Excellent! Sorry for missing this.

@unutbu, any chance of adding support for shows not available as a torrent?
I watch a few Rev3 shows and was going to try this script:  [http://revision3.com/forum/showthread.php?t=25019](http://revision3.com/forum/showthread.php?t=25019)

---

### Post by unutbu on 2009-11-05
> ImportError: No module named feedparser

Yes, I changed the script from using beautifulsoup to
feedparser. I thought I could make the change without affecting anybody, but obviously, I was wrong! (I didn't realize that python-feedparser did not come with the standard installation of python.) Sorry about that. 

>  Put the URL in quotes "example.com"
Thank you, abhiroopb.

> 
any chance of adding support for shows not available as a torrent?

@KillaB7: I've poked around the revision3.com web site and it appears to organize its shows in a way which is very different than an rss feed with a list of .torrent links. 
My script is no where near the right tool for scraping revision3.com.

---

### Post by KillaB7 on 2009-11-05
> **unutbu said:**
> 
@KillaB7: I've poked around the revision3.com web site and it appears to organize its shows in a way which is very different than an rss feed with a list of .torrent links. 
My script is no where near the right tool for scraping revision3.com.

Sorry for not giving an example feed to look at.  I would figure you could just add a CLI switch to download a different file type.

```

tormon.py -O /path/to/downloaded/diggnation/files -filetype WMV -u "http://revision3.com/diggnation/feed/WMV-Large"

```

Or is is more complicated than that?

---

### Post by unutbu on 2009-11-05
Okay, [the script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") now has the the ability to download wmv files from [http://revision3.com/diggnation/feed/WMV-Large](http://revision3.com/diggnation/feed/WMV-Large). To do so, use the command
```

tormon.py -f wmv -u "http://revision3.com/diggnation/feed/WMV-Large"
```

Note "-f wmv" means that only files that end with "wmv" or "WMV" will be downloaded.

If a web page has both wmv and avi files on it, you can use two -f flags:
```

tormon.py -f wmv -f avi -u "http://revision3.com/diggnation/feed/WMV-Large"
```

In other words, you can have multiple -f flags, just like you can have multiple -u flags.

I've tested that tormon (still) works with the following commands:
```

tormon.py -u "http://ezrss.it/search/index.php?show_name=dexter&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss" -u "http://ezrss.it/search/index.php?show_name=how+i+met+your+mother&show_name_exact=true&date=&quality=HDTV&quality_exact=true&release_group=&mode=rss"

tormon.py -u "http://www.ezrss.it/search/index.php?show_name=Smallville"
```

To get tormon to work with revision3.com, I had to switch back to using BeautifulSoup.

So apologies to those of you who have downloaded the python-feedparser package.

We are back with python-beautifulsoup, and that's where we'll be staying (for the foreseeable future) since it is a bit more versatile.

Oh, also: the -O flag is now optional. If you omit it, the files will be placed in ~/Desktop.

---

### Post by KillaB7 on 2009-11-05
Just tried on the smallest set of wmv files I could find, but getting the following error:

```
jack@Karmic:/$ tormon.py -O /mnt/storage2/Media/Videos/Revision3 -f wmv -u "http://revision3.com/bestof/feed/WMV-Small"
RSS feed: http://revision3.com/bestof/feed/WMV-Small
Downloading /mnt/storage2/Media/Videos/Revision3/pts/redirect.wmv/bitcast-a.bitgravity.com/revision3/web/bestof/0425/bestof--0425--bytejacker-0007--small.wmv9.wmv
Traceback (most recent call last):
  File "/bin/tormon.py", line 122, in <module>
    Main()  
  File "/bin/tormon.py", line 116, in __init__
    self.parse_rss_feed()
  File "/bin/tormon.py", line 104, in parse_rss_feed
    self.download_torrent(link)
  File "/bin/tormon.py", line 82, in download_torrent
    fh=open(target_file,'w')
IOError: [Errno 2] No such file or directory: u'/mnt/storage2/Media/Videos/Revision3/pts/redirect.wmv/bitcast-a.bitgravity.com/revision3/web/bestof/0425/bestof--0425--bytejacker-0007--small.wmv9.wmv'

```

Could it be the redirection that's throwing things off?

---

### Post by abhiroopb on 2009-11-05
Thanks for the updates unutbu.

One smallish problem regarding the error script. Basically, I run my script every five minutes 24 hours a day seven days a week. Its not really a problem since most of the time it comes up empty (except when one of my feeds obviously updates).

Now each time the script runs (i.e. 12 times an hour) the error log appends all the errors. So, essentially, every hour I have the same list of errors repeated 12 times.

I'm not really sure what the best solution to this would be. Obviously deleting the error log or even purging it does not serve the purpose. 

The best thing I can think of is adding the list of torrent files that are having an error into the already downloaded torrent files list. So, the first time they run they would show up as an error, but the next time it would seem as though they were already downloaded. Does that make sense?

Thanks!

---

### Post by unutbu on 2009-11-05
KillaB7, yep, you found a bug! It has been fixed.

abhiroopb, the script now reports each error once and only once. If at some point it succeeds in downloading a file that had failed before, it removes the url from the error log and adds it to the downloaded files log.

You know [the drill]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19").

---

### Post by abhiroopb on 2009-11-05
Thanks, just tested it and it works perfectly! But, the script still displays the "failed to download". This doesn't really matter though as the script mostly runs in the background anyway.

Thanks!

---

### Post by KillaB7 on 2009-11-05
Thanks again unutbu!
That -f flag is great.  Just tested on an .mp4 feed without a hitch.

Any chance of adding a batch file flag to better manage the string length?

So as an alternative to:
```

tormon.py -u "http://rss.feed1" -u "http://rss.feed2"

```

You could run:
```

tormon.py -O /path/to/downloaded/dot/torrent/files -b /path/to/torrent_feeds.txt

```

Or by extension:
```

tormon.py -O /path/to/downloaded/media/files -f mp4 -f wmv -f mp3 -b /path/to/direct_feeds.txt

```

---

### Post by unutbu on 2009-11-05
LOL, that's a good idea. Thanks KillaB7.

Now you can create a file with a list of all the rss feeds (urls) you wish to monitor.
Put one url per line. If you put the list of urls in /path/to/torrent_feeds.txt
then 
```

tormon.py -b /path/to/torrent_feeds.txt
```

will download .torrents (or other files) to ~/Desktop.

---

### Post by unutbu on 2009-11-05
> **abhiroopb said:**
> But, the script still displays the "failed to download".

I've commented out the "tormon failed to download ..." message.
The errors are now only in the error log file.

---

### Post by KillaB7 on 2009-11-06
Working great here.

Sorry for all the extra work unutbu, it's very much appreciated :popcorn:

The only other feature I can think of that would be handy for first runs would be a dummy parse mode (ie. parse and update .downloaded_torrents without actually downloading any torrent/media files).

---

### Post by KillaB7 on 2009-11-06
For anyone interested, here's a howto (and more importantly an init script) on setting up a Deluge backend.
[http://apocryph.org/2008/11/30/setting_deluge_headless_ubuntu_seedbox_windows_client/](http://apocryph.org/2008/11/30/setting_deluge_headless_ubuntu_seedbox_windows_client/)

---

### Post by unutbu on 2009-11-06
I've added a "-m" flag to [the script ]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") which adds all torrents/files found to the log of downloaded files.

When you run
```

tormon.py -m -b direct_feeds.txt
```

tormon slurps all the .torrents that it finds in the rss feeds 
and adds them to the log of downloaded files, and removes them (if they exist)
from the error log.

This is a way to tell tormon that you are currently up-to-date.

I hope this is what you were looking for, KillaB7.

By the way, you can get a help summary of all the options by typing
```

tormon.py -h
```

---

### Post by mobilediesel on 2009-11-06
> **unutbu said:**
> I've added a "-m" flag to [the script ]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") which adds all torrents/files found to the log of downloaded files.

When you run
```

tormon.py -m -b direct_feeds.txt
```

tormon slurps all the .torrents that it finds in the rss feeds 
and adds them to the log of downloaded files, and removes them (if they exist)
from the error log.

This is a way to tell tormon that you are currently up-to-date.

I hope this is what you were looking for, KillaB7.

By the way, you can get a help summary of all the options by typing
```

tormon.py -h
```

I've been using [bashpodder]("http://lincgeek.org/bashpodder/") for downloading my podcasts. Now that you've added the **-m** option, this script will be much more useful than bashpodder. I can set up a text file for each type of download whether audio, video or torrent and even set up different files for daily, weekly or monthly updates.

This script isn't much more complicated than bashpodder but it's tons more flexible! Thanks for doing all the work in Python that I was trying to figure out in Bash. :D

Actually the only thing I can think of to add is the ability to have comments in the text file containing rss urls.
For example:
```
#The following is the escape pod podcast.
http://escapepod.org/podcast.xml
```

---

### Post by unutbu on 2009-11-07
mobilediesel, thanks for the kind words and for the suggestion. [The script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") can now handle comments in the rss feed batch file. Comments are any line that begins with a # character.
> 
Thanks for doing all the work in Python

Yep, Python is just incredibly easy and [fun to use]("http://xkcd.com/353/"). :)

---

### Post by mobilediesel on 2009-11-07
> **unutbu said:**
> mobilediesel, thanks for the kind words and for the suggestion. [The script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") can now handle comments in the rss feed batch file. Comments are any line that begins with a # character.


Yep, Python is just incredibly easy and [fun to use]("http://xkcd.com/353/"). :)

Excellent work! That script is short enough that it'll help me learn Python while I compare its output to bashpodder's output.
I usually default to bash scripting when I do anything just because most of the stuff I do isn't large scale.

XKCD has to be one of the best, if not THE best, online comics!

---

### Post by damnandy on 2009-11-12
LOVIN' the -f feature unutbu!!!!


But can it be used to parse feeds with download.php??

I am using a feed for a private tracker that uses download.php on each RSS entry.



THANKS!!!!

---

### Post by unutbu on 2009-11-14
damnandy, when you try to download multiple files called download.php, is the problem that you only end up with one?
Or are you ending up with none?

---

### Post by damnandy on 2009-11-14
> **unutbu said:**
> damnandy, when you try to download multiple files called download.php, is the problem that you only end up with one?
Or are you ending up with none?



I end up with none, the feed is recognized and there is a pusing while it searches it but no dowload at all.

---

### Post by unutbu on 2009-11-15
damnandy, I'm going to need some more information to work on this problem.
Can you send me a link to the rss feed, or use [http://paste.ubuntu.com/](http://paste.ubuntu.com/) to post the contents of an rss feed containing download.php links?

---

### Post by damnandy on 2009-11-15
The URL for the feed is [http://www.nhltorrents.co.uk/rssteams.php?team=16](http://www.nhltorrents.co.uk/rssteams.php?team=16)

---

### Post by unutbu on 2009-11-16
Hm, this feed appears to be blank for me... :confused:

---

### Post by KillaB7 on 2009-11-16
Just checked memory usage on my server and noticed that mem and swap were both maxed out.  Ran "ps -ef | grep python" and found many tormon.py entries.
Anyone else seeing the same?

EDIT: Might be a 9.10 thing.  I just installed some python updates.

---

### Post by damnandy on 2009-11-16
Damn, its a private tracker that requires authentication. 

Ill see if i can find another example.

---

### Post by KillaB7 on 2009-11-17
Finally found my problem. The Revision3 feed redirected to a different mirror and started to download many GBs.
It appears they have at least four mirrors (bitcast-a through d).

unutbu, is this the problem you warned me about with Rev3's servers?
Is logging just the filename vs. entire URL a good or bad idea?

---

### Post by KillaB7 on 2009-11-17
> **KillaB7 said:**
> 
Is logging just the filename vs. entire URL a good or bad idea?

Another if/else perhaps :lolflag:

No switch = full URL logged to file
Switch = only the filename logged to file

---

### Post by unutbu on 2009-11-19
KillaB7, yep, it's that time of year again... [tormon]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") needs a new switch!

Introducing the dulcet-sounding (haha)
```

tormon.py --match_by_filename
```

When you use this switch, tormon will consider a file as having been already downloaded
as long as the filename matches the filename of a URL in the download log. (Full urls are still being saved in the download log. Having one download log with both urls and bare filenames I think would be a bad design decision.)

As with all long switch names, you can shorten it to a shorter string as long as it uniquely specifies a switch. For example,
```

tormon.py --mat
```

also works. Notice long switch names require two hyphens. (The -m switch is already being used, and --mat is the shortest switch that disambiguates --match_by_filename from --mark_all_downloaded.)

If you have a suggestion for a better name/letter for the switch, let me know. I'm open to suggestions.

---

### Post by KillaB7 on 2009-11-19
Muchas gracias!
Very nicely done.

I think I'm really out of new switch ideas this time.

---

### Post by mobilediesel on 2009-11-21
> **unutbu said:**
> KillaB7, yep, it's that time of year again... [tormon]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") needs a new switch!

Introducing the dulcet-sounding (haha)
```

tormon.py --match_by_filename
```

When you use this switch, tormon will consider a file as having been already downloaded
as long as the filename matches the filename of a URL in the download log. (Full urls are still being saved in the download log. Having one download log with both urls and bare filenames I think would be a bad design decision.)

As with all long switch names, you can shorten it to a shorter string as long as it uniquely specifies a switch. For example,
```

tormon.py --mat
```

also works. Notice long switch names require two hyphens. (The -m switch is already being used, and --mat is the shortest switch that disambiguates --match_by_filename from --mark_all_downloaded.)

If you have a suggestion for a better name/letter for the switch, let me know. I'm open to suggestions.

You could make that option capital **M** instead of the already-used lowercase **m**. I tend to use the long switch names whenever available for ANY command line stuff I use. It's easier to debug when I screw things up later. :D

It's better in the long run to use long switch names when setting up with cron or calling from another script. When something goes wrong, you don't have to remember what various letters mean when you can just spell it out.

Not that there's anything wrong with the single-letter switches. Those are perfect for typing something one time in the terminal.

---

### Post by unutbu on 2009-11-21
> **mobilediesel said:**
> You could make that option capital **M** instead of the already-used lowercase **m**.

Done. :) 
In the new version of [the script]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19"), "-M" is now a synonym for --match_by_filename.

---

### Post by MasterOfTheHat on 2009-12-07
Friggin amazing, unutbu! Many thanks!

---

### Post by abhiroopb on 2010-01-18
Any suggestions for a substitute for EZTV/EZRSS? These seem to be down for quite a while.

---

### Post by mobilediesel on 2010-01-18
> **abhiroopb said:**
> Any suggestions for a substitute for EZTV/EZRSS? These seem to be down for quite a while.

They appear to be back: [http://twitter.com/eztv_it/status/7869822635](http://twitter.com/eztv_it/status/7869822635)

I've been relying on eztv since Mininova eliminated most of their content. I hope that kind of downtime doesn't happen again.

---

### Post by abhiroopb on 2010-01-18
No new updates :(

---

### Post by cbaughman on 2010-02-02
Great script i'm going to implement it when I get home from work. The one option I would find useful would be a search for show option. uTorrent has this feature where you can set it to monitor an rss feed but only download files with a given file name (or part of a file name). 

Thank you again

---

### Post by ErwinJunge on 2010-02-15
Thank you very much for this unutbu. I've never added so much torrents to quickly to transmission as with this.

I just want to point out 1 thing:

You typed MAILTO=USER etc
I think you can also simply do MAILTO=me@example.com Then you don't need to have the mail stuff running (trying it myself now).

Anyways, great tool, great instructions. Keep up the good work!

Edit: Apparently my idea was wrong. MAILTO=me@example.com doesn't work. I'll look in to how to mail myself from cron later (have to work now). On the plus side: The script in combination with Transmission definitely works (it added a new episode of Lost Season 6 to Transmission earlier today).

---

### Post by vollucris on 2010-05-01
Hey guys, why don't you try using qBitTorrent. It has the RSS Feeds built in and the interface and options are very close to those of uTorrent from Windows, actually they advertise it as a uTorrent clone.
I've been using it for quite a while now and it works flawlessly! Give it a try!
 
------------------
...and Linux for All!

---

### Post by Greblok on 2010-05-23
I hate to bump threads, but I just have to say:

> **vollucris said:**
> Hey guys, why don't you try using qBitTorrent.

Thank you!!! Finally...

---

### Post by marcsherman on 2010-07-28
Is there any way to disable the file-type filtering? EZTV sometimes posts torrents with URLs without any extension, just an 8 hex digit file name part. They are torrent files, just not named like them.  For example: [http://re.zoink.it/4c4cff60](http://re.zoink.it/4c4cff60) 

I tried adding -f "", but it doesn't work:
[HTML]
Downloading /var/lib/transmission-daemon/watch/
Traceback (most recent call last):
  File "/usr/local/bin/tormon.py", line 159, in <module>
    Main()
  File "/usr/local/bin/tormon.py", line 153, in __init__
    self.parse_rss_feed()
  File "/usr/local/bin/tormon.py", line 141, in parse_rss_feed
    self.download_torrent(link)
  File "/usr/local/bin/tormon.py", line 107, in download_torrent
    fh=open(target_file,'w')
IOError: [Errno 21] Is a directory: u'/var/lib/transmission-daemon/watch/'
[/HTML]

---

### Post by marcsherman on 2010-07-28
> **marcsherman said:**
> Is there any way to disable the file-type filtering? EZTV sometimes posts torrents with URLs without any extension, just an 8 hex digit file name part. They are torrent files, just not named like them.  For example: [http://re.zoink.it/4c4cff60](http://re.zoink.it/4c4cff60) 


I figured out the problem. The feed included a link to the full feed itself, which tormon was trying to download. I filter out urls with no file name part, and if there is a filename part but it has no extension, I append ".torrent" when I download it. Here's the patch:

[HTML]
--- tormon.py.orig      2010-07-28 22:23:50.643729900 -0400
+++ tormon.py   2010-07-28 22:21:25.013786384 -0400
@@ -92,6 +92,12 @@
         except ValueError:
             pass
     def download_torrent(self,url):
+        filename=self.url2filename(url)
+        if (filename==''):
+            print('Skipping empty url: %s'%url)
+            return
+        if (filename.find('.')==-1):
+            filename=filename+'.torrent'
         try:
             sock=urllib2.urlopen(url)
         except (HTTPError, URLError):
@@ -99,9 +105,9 @@
             if url not in self.errors:
                 self.errors.append(url)
         else:
-            filename=self.url2filename(url)
             target_file=os.path.join(self.opt.output_dir,filename)
             print('Downloading %s'%target_file)
+            print('from %s'%url)
             content=sock.read()
             sock.close()
             fh=open(target_file,'w')
[/HTML]

---

### Post by BklynKid on 2010-08-30
Nice job on the script unutbu. Thank you! :popcorn:

---

### Post by rampageoberon on 2010-11-01
Incase anyone comes across this thread and wants another script/solution you can have a look at [http://rampage.homelinux.com/scripts/rss-tor-dl.html](http://rampage.homelinux.com/scripts/rss-tor-dl.html)

Its written in Perl.

Cheers,

---

### Post by ccool on 2010-11-20
Thank you a thousand unutbu, very nice script.

---

### Post by deoren on 2010-12-12
Hey guys,

I don't know if unutbu is still maintaining tormon.py or not, but there is a similar python script available: [Synclosure]("http://projects.whyaskwhy.org/projects/synclosure/").

The project has been around since 2004 and just recently changed hands. A new release is coming up soon.

Here's a pre-0.2 snapshot if you're interested:
[http://sourceforge.net/projects/synclosure/files/releases/testing/pre-0.2/](http://sourceforge.net/projects/synclosure/files/releases/testing/pre-0.2/)


If you come across any problems with it, please [submit a bug]("http://projects.whyaskwhy.org/projects/synclosure/") so they can be fixed.


Previous homepage:
[http://raphb.ch/c/synclosure](http://raphb.ch/c/synclosure)

 Current homepage:
[http://projects.whyaskwhy.org/](http://projects.whyaskwhy.org/)
                  
Twitter:
[http://twitter.com/synclosure](http://twitter.com/synclosure)

SourceForce.net downloads:
[http://sourceforge.net/projects/synclosure/](http://sourceforge.net/projects/synclosure/)

unutbu, what license is tormon.py released under? There may be some features that it has which would benefit Synclosure.

Edit: Synclosure 0.2 has been released. See [this post]("/showpost.php?p=10252652&postcount=102") for more details.

---

### Post by uriel1998 on 2010-12-13
Personally, I use [FlexGet]("http://flexget.com/") to get the RSS feeds.  It's lightweight and called by a cron job - but has a lot of power and options should I need them.  It's another solution.

---

### Post by deoren on 2010-12-18
I'll have to give FlexGet a look. The feature list is really impressive.

I wanted to followup on my earlier post about Synclosure and mention that a 0.2 release is out.

[LIST]
[*][Announcement]("http://projects.whyaskwhy.org/news/5")
[*][Project page]("http://projects.whyaskwhy.org/projects/synclosure/")
[*][Twitter]("http://twitter.com/synclosure")
[/LIST]

I'll refrain from posting further about it unless there are any questions/comments relating to it.

Thanks.

---

### Post by expirobo on 2011-10-01
Hey I added Regex for those of you who belong to RSS feeds for a show. If the tracker puts out multiple variations of an episode, you can use Regular Expressions to parse the feeds. 

So for an episode in which you want 720p with a filename like:
Simpsons.S01E03.Title.720p.HDTV.stuffhere.torrent
but not:
Simpsons.S01E03.Title.720p.HDTV.WEBdl.stuffhere.torrent

Use this regex
```
^(?=.*?(?i)s[0-9]{2})(?=.*?(?i)e[0-9]{2})(?=.*?(?i)720)(?=.*?(?i)720)((?![/QUOTE](?i)web).)*$
```

So use this:

```
tormon.py -O "/downloaddir" -u "http://tracker.com/rss_favorites.php"
 -r "^(?=.*?(?i)s[0-9]{2})(?=.*?(?i)e[0-9]{2})(?=.*?(?i)720)(?=.*?(?i)720)((?!(?i)web).)*$"
```

[PHP]#!/usr/bin/env python 

import urllib2,urlparse 
from urllib2 import HTTPError,URLError 
from BeautifulSoup import BeautifulSoup 
import os
import re
import optparse 

__usage__=''' 
tormon.py -O ~/test/tormon -u "http://rss.feed" 
''' 

class Main(object): 
    ''' 
    tormon checks an rss feed for new torrents. When it finds a new .torrent, to 
    downloads it to a specified output directory, where (presumably) a monitoring 
    torrent program will download the corresponding file.     
    ''' 
    def parse_options(self): 
        usage = 'usage: %prog [options]'+__usage__ 
        parser = optparse.OptionParser(usage=usage) 
        parser.add_option( 
            '-O', '--output_dir', dest='output_dir',  
            help='directory into which new torrents are saved',  
            metavar='DIR') 
        parser.add_option( 
            '-f', '--filetype', dest='filetype', 
            action='append', 
            default=[], 
            help='admissible file types',  
            metavar='TYPE') 
        parser.add_option( 
            '-d', '--downloaded_torrents', dest='downloaded_torrents', 
            default=os.path.expanduser('~/.downloaded_torrents'), 
            help='log of already downloaded torrents',  
            metavar='FILE') 
        parser.add_option( 
            '-e', '--error_log', dest='error_log', 
            help='log of torrents tormon failed to download',  
            metavar='FILE') 
        parser.add_option( 
            '-b', '--batch', dest='batch', 
            help='file containing list of rss feed urls',  
            metavar='FILE')
        parser.add_option( 
            '-r', '--regex', dest='regex', 
            help='regular expression for matching torrents',  
            metavar='FILE')  
        parser.add_option( 
            '-u', '--url', dest='url', 
            action='append', 
            default=[], 
            help='url of the rss feed',  
            metavar='URL') 
        parser.add_option( 
            '-m','--mark_all_downloaded', dest='mark_all_downloaded', 
            action='store_true',  
            default=False, 
            help="mark all torrents as already downloaded") 
        parser.add_option( 
            '-M','--match_by_filename', dest='match_by_filename', 
            action='store_true',  
            default=False, 
            help="recognize downloaded files by filename, not URL. Matching by URL is the default.")         
        (self.opt, args) = parser.parse_args() 
        if self.opt.batch: 
            for line in open(self.opt.batch,'r'): 
                line=line.strip() 
                if line and not line.startswith('#'): 
                    self.opt.url.append(line) 
        if not self.opt.output_dir: 
            self.opt.output_dir=os.path.expanduser('~/Desktop') 
        if not self.opt.filetype: 
            self.opt.filetype=['.torrent'] 
        if not self.opt.error_log: 
            self.opt.error_log=self.opt.downloaded_torrents+'.errors' 
        try: 
            os.makedirs(self.opt.output_dir) 
        except OSError: 
            if not os.path.exists(self.opt.output_dir): 
                print('tormon failed to create directory %s'%self.opt.output_dir) 
                exit(1) 
    def load_list_of_already_downloaded_torrents(self): 
        try: 
            self.downloaded=open(self.opt.downloaded_torrents,'r').read().split() 
        except IOError: 
            self.downloaded=[] 
        try: 
            self.errors=open(self.opt.error_log,'r').read().split() 
        except IOError: 
            self.errors=[] 
    def update_downloaded(self,url): 
        self.downloaded.append(url) 
        try: 
            self.errors.remove(url) 
        except ValueError: 
            pass  
    def regex(self,filename): 
        if self.opt.regex: 
            pattern=self.opt.regex 
        else: 
            pattern='.*' 
        matches=re.search(pattern,filename) 
        if matches: 
            return(1) 
    def download_torrent(self,url): 
        try: 
            sock=urllib2.urlopen(url) 
        except (HTTPError, URLError): 
            # print('tormon failed to download %s'%url) 
            if url not in self.errors: 
                self.errors.append(url) 
        else: 
            filename=self.url2filename(url) 
            if self.regex(filename):
            	target_file=os.path.join(self.opt.output_dir,filename) 
            	print('Found match and downloading %s'%target_file) 
            	content=sock.read() 
            	sock.close() 
            	fh=open(target_file,'w') 
            	fh.write(content) 
            	fh.close() 
            self.update_downloaded(url) 
    def url2filename(self,url): 
        return os.path.basename(urlparse.urlparse(url)[2]) 
    def has_been_downloaded(self,url): 
        if self.opt.match_by_filename: 
            filename=self.url2filename(url) 
            return (filename in [self.url2filename(link) for link in self.downloaded]) 
        else: 
            return (url in self.downloaded) 
    def parse_rss_feed(self): 
        for url in self.opt.url: 
            print('RSS feed: %s'%url) 
            try: 
                sock=urllib2.urlopen(url) 
            except (HTTPError, URLError): 
                print('tormon failed to download %s'%url) 
            else: 
                content=sock.read() 
                sock.close() 
                soup=BeautifulSoup(content) 
                links=([link.nextSibling for link in soup.findAll('link')]+ 
                       [link['href'] for link in soup.findAll('a')]+ 
                       [link['url'] for link in soup.findAll('media:content')]) 
                for link in links: 
                    if (any([link.lower().endswith(ending) 
                             for ending in self.opt.filetype]) 
                        and not self.has_been_downloaded(link)): 
                        if self.opt.mark_all_downloaded: 
                            print('Marking %s as downloaded'%link) 
                            self.update_downloaded(link) 
                        else: 
                            self.download_torrent(link) 
    def save_list_of_already_downloaded_torrents(self): 
        fh=open(self.opt.downloaded_torrents, 'w') 
        fh.write('\n'.join(self.downloaded)) 
        fh.close() 
        fh=open(self.opt.error_log, 'w') 
        fh.write('\n'.join(self.errors)) 
        fh.close() 
    def __init__(self): 
        self.parse_options()         
        self.load_list_of_already_downloaded_torrents() 
        try: 
            self.parse_rss_feed() 
        except KeyboardInterrupt: 
            pass 
        finally: 
            self.save_list_of_already_downloaded_torrents() 
if __name__=='__main__': 
    Main()  
[/PHP]

---

### Post by KillaB7 on 2011-10-13
I've been using tormon to download Rev3 shows without trouble for ages now, but would like to rid myself of a couple of their shows major bias towards Apple and start watching TWiT instead.
The only problem is that the TWiT RSS feed url contains a variety of different bitrates of the same episode.
Anyone know of any parsing tricks (subdirectory feed, &, etc.) that can be done via the url?

[http://feeds.twit.tv/twit_video_large](http://feeds.twit.tv/twit_video_large)

---

### Post by expirobo on 2011-10-13
> **KillaB7 said:**
> I've been using tormon to download Rev3 shows without trouble for ages now, but would like to rid myself of a couple of their shows major bias towards Apple and start watching TWiT instead.
The only problem is that the TWiT RSS feed url contains a variety of different bitrates of the same episode.
Anyone know of any parsing tricks (subdirectory feed, &, etc.) that can be done via the url?

[http://feeds.twit.tv/twit_video_large](http://feeds.twit.tv/twit_video_large)

Try looking at the post right above yours. Use regular expressions to parse feeds. You can always add your own variation to this code. Its really straightforward.

---

### Post by KillaB7 on 2011-10-13
> **expirobo said:**
> Try looking at the post right above yours. Use regular expressions to parse feeds. You can always add your own variation to this code. Its really straightforward.

I did see your post, but was hoping someone might know of a server side implementation. Sorry for not testing before commenting. Your contribution is definitely appreciated and I'll be sure to test it asap. Thanks!

---

### Post by KillaB7 on 2011-10-23
I'm trying, but I can't quite figure out how to get tormon and REGEX working successfully with [http://feeds.twit.tv/twit_video_large](http://feeds.twit.tv/twit_video_large)

I've only ever used grep until now, so it's quite likely that my regex syntax is wrong.

Here's the full CLI command I've been trying (NOTE: I'm using the -m option for obvious reasons. That wouldn't affect the regex portion of the script, would it?):

```
./tormon.py -u http://feeds.twit.tv/twit_video_large -d /home/jason/testdl.txt -f mp4 -m -r "^(?=.*?h264b_864x480_500).*$" -M
```

---

### Post by Weidbrewer on 2011-11-14
> **expirobo said:**
> Hey I added Regex for those of you who belong to RSS feeds for a show. If the tracker puts out multiple variations of an episode, you can use Regular Expressions to parse the feeds. 

So for an episode in which you want 720p with a filename like:
Simpsons.S01E03.Title.720p.HDTV.stuffhere.torrent
but not:
Simpsons.S01E03.Title.720p.HDTV.WEBdl.stuffhere.torrent

Use this regex
```
^(?=.*?(?i)s[0-9]{2})(?=.*?(?i)e[0-9]{2})(?=.*?(?i)720)(?=.*?(?i)720)((?!(?i)web).)*$
```
[/QUOTE]

Wow.

Okay, I understood what some (not much) of that regex does.  "(?=.*?(?i)720)" takes out anything that says "720" in the feed, right?  I'm not sure what the rest does, especially the "(?![/QUOTE](?i)web)" part.

I'm trying to set up a filter for my RSS in Ktorrent, much like earlier posts, just to eliminate hits for 720p feeds, but I can't get any regex's to work...Is that what this code would accomplish?

EDIT:  I see that the code broke the "quote" feature of the forum.  I am referring to the code above after "Use this regex" in expirobo's post from Oct 1st.

---

### Post by sbjaved on 2012-02-26
for ppl who download torrents off eztv, check out [my script]("http://sbjaved.blogspot.com/2012/02/eztv-feed-parser-4.html")

---

### Post by Schrodinger's Cat on 2012-04-14
> **unutbu said:**
> 
[*] It will save a list of the urls of successfully downloaded torrents to ~/.downloaded_torrents.

This script is great! I don't know if it's still being maintained at all... but if so, would it be possible to have it purge files from the .downloaded_torrents list after they no longer appear in the RSS, just to keep the file from ballooning out of control?

---

### Post by sbjaved on 2012-11-03
you can use karmorra to get all your eztv feeds in one place and download torrents using this [script]("http://koogee.wordpress.com/").

---

