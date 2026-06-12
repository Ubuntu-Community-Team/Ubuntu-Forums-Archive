---
title: "Banning an IP Address?"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Hopkins on 2007-04-30
Hi,

I've been running my own personal Ubuntu server for six months or so now, and I love it!  However, it seems to attract script kiddies all the time :P  The current one has been going for days, a different password every two seconds or so.  The hard disk is blipping every time as it makes the log entry.  Whilst it is very satisfying to know that Ubuntu (and my passwords!) can take this abuse, it is rather annoying.  The guy's specifically trying to get into my vsftpd based ftp site, but is there a way to put in place some general remote access policy regardless of what someone is trying to log into?  Something along the lines of 10 false attempts from a single IP address will result in a ban and all future requests will be ignored would be ideal.

I've spent a while trying to locate this information for myself, but I cannot find any forum posts asking a similar question!  Does no-one else suffer from this problem?

Cheers.

---

### Post by Lord Illidan on 2007-04-30
Are you using the command line to administrate the server? Why not learn more about iptables, the linux firewall here : [http://www.netfilter.org/documentation/index.html#documentation-faq](http://www.netfilter.org/documentation/index.html#documentation-faq)

Otherwise, if you are using a GUI, try using firestarter..

---

### Post by Hopkins on 2007-04-30
Thanks for the suggestion - I will do that!  This server is command line only.  I'd heard netfilter mentioned in relation to the Ubuntu Desktop that I'm trying on my laptop, but it had only been in passing and I hadn't followed it up.

---

### Post by Hopkins on 2007-04-30
Wow, that seems to be a pretty powerful system.  It's going to take a bit more reading though ;)  I was trying to work out if I can achieve my aim using the "-m state" option, but it seems my brain is demanding I sleep now.  Damn brain.

---

### Post by Hopkins on 2007-05-02
I seem to be able to do all sorts of fancy stuff with iptables, such as "limit the number of new incoming connections in a given time period", but I can't figure out how to say "limit the number of new incoming connections in a given time period per IP address".  Maybe I would have to do something like create a chain that will write an IP address to a log file if it connects too frequently and then have another chain forbid any IP addresses in the log file...  If so it seems like quite a long-winded way to perform what must surely be a common function.

Am I missing something?

Thanks!

---

### Post by octoberdan on 2007-05-02
> **Hopkins said:**
> Hi,

I've been running my own personal Ubuntu server for six months or so now, and I love it!  However, it seems to attract script kiddies all the time :P  The current one has been going for days, a different password every two seconds or so.  The hard disk is blipping every time as it makes the log entry.  Whilst it is very satisfying to know that Ubuntu (and my passwords!) can take this abuse, it is rather annoying.  The guy's specifically trying to get into my vsftpd based ftp site, but is there a way to put in place some general remote access policy regardless of what someone is trying to log into?  Something along the lines of 10 false attempts from a single IP address will result in a ban and all future requests will be ignored would be ideal.

I've spent a while trying to locate this information for myself, but I cannot find any forum posts asking a similar question!  Does no-one else suffer from this problem?

Cheers.

Quick fix:
[http://www.linuxforums.org/forum/ubuntu-help/78872-how-ban-ip-vsftpd.html](http://www.linuxforums.org/forum/ubuntu-help/78872-how-ban-ip-vsftpd.html)

---

### Post by TauRush on 2007-05-07
I was looking for a script to stop those ftp attacks some time ago and found a possible solution at a Gentoo forum.
Although I am not using Gentoo (but Fedora) I gave the script a try.
After fixing some small issues and adding a permanent banlist, I have it working at home and at the office for some time now.
I am running the script every 2 minutes through a cronjob, to keep the amount of attacks small and also my logfiles don't overflow.

Thanks to destuxor for the initial setup of the script.

Here is my adjusted script for all to use. 


```

#!/usr/bin/perl -w
# destuxor (wjholden@gmail.com) - 4/26/2006
# TauRush (snakesandarrows@gmail.com) - 3/17/2007
# A simple script to go through a VSFTPD log and block people who have
# unsuccessfully attempted to log in.

#configuration options:
$logfilename = '/var/log/vsftpd/vsftpd.log'; # location of your logfile.
$allow_exceptions = 1; # if you wish to specify a file to put exceptions into,
                       # say 1 here, otherwise put 0.
$exception_file = '/var/log/vsftpd/banned.log';  # if you said 1 above, put your filename here.
$max_failures = 5;    # maximum number of failures someone can have before
                       # getting blocked.
#end of configuration options

$command = 'grep \'FAIL LOGIN\' '.$logfilename.' | sed -r \'s/^.{0,}Client .//\' | sed -r \'s/\"//\' | uniq -c';

@connected_ips = `$command`;


undef %noblock;
if ($allow_exceptions == 1) {
    open (FH, $exception_file) or die "$!\n";
    @exceptions = <FH>;
    close (FH);
}

foreach $ip (@exceptions) {
# Added by TauRush to chop LF character
    chop ($ip);
    $noblock{"$ip"} = 1;
}

foreach $host (@connected_ips)
{
    @info = split(/\s+/, $host);
    if (($info[1] > $max_failures) and !$noblock{$info[2]}) {
        system("/sbin/iptables -I INPUT 1 -s $info[2] -j DROP");
# 3 lines added by TauRush to create banned.log file
        open FILE,">>$exception_file" or die "Unable to open file!\n";
        print FILE "$info[2]\n";
   close FILE;
    }
} 

```

---

### Post by outz on 2008-01-10
TauRush, thanks for the script... it has been extremely helpful in blocking the brute force attacks on my vsftpd server.

I have modified the script to log the ip's being blocked to a file as well as time stamp them. I'm new to perl, but the changes I made seem to work.

```


#!/usr/bin/perl -w
# destuxor (wjholden@gmail.com) - 4/26/2006
# TauRush (snakesandarrows@gmail.com) - 3/17/2007
# outz (ubuntu@outz.com)- 1/09/2008
# A simple script to go through a VSFTPD log and block people who have
# unsuccessfully attempted to log in.

#configuration options:
$logfilename = '/var/log/vsftpd.log'; # location of your logfile.


# 1 line added by outz to create a file to store ip's being blocked

$blocked = '/var/log/blocked-ips.log'; # location to log ip's that were blocked

# 5 lines added by outz to create a timestamp for the blocked-ips.log

@months = qw(Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec);
@weekDays = qw(Sun Mon Tue Wed Thu Fri Sat Sun);
($second, $minute, $hour, $dayOfMonth, $month, $yearOffset, $dayOfWeek) = localtime();
$year = 1900 + $yearOffset;
$theTime = "$hour:$minute:$second, $weekDays[$dayOfWeek] $months[$month] $dayOfMonth, $year";

$allow_exceptions = 1; # if you wish to specify a file to put exceptions into,
                       # say 1 here, otherwise put 0.
$exception_file = '/var/log/banned.log';  # if you said 1 above, put your filename here.
$max_failures = 5;    # maximum number of failures someone can have before
                       # getting blocked.
#end of configuration options

$command = 'grep \'FAIL LOGIN\' '.$logfilename.' | sed -r \'s/^.{0,}Client .//\' | sed -r \'s/\"//\' | uniq -c';

@connected_ips = `$command`;


undef %noblock;
if ($allow_exceptions == 1) {
    open (FH, $exception_file) or die "$!\n";
    @exceptions = <FH>;
    close (FH);
}

foreach $ip (@exceptions) {
# Added by TauRush to chop LF character
    chop ($ip);
    $noblock{"$ip"} = 1;
}

foreach $host (@connected_ips)
{
    @info = split(/\s+/, $host);
    if (($info[1] > $max_failures) and !$noblock{$info[2]}) {
        system("/sbin/iptables -I INPUT 1 -s $info[2] -j DROP");

# 3 lines added by outz to write the blocked ip along with a timestamp to blocked-ips.log
        open FILE,">>$blocked" or die "Unable to open file!\n";
        print FILE "$theTime $info[2]\n";
   close FILE;

# 3 lines added by TauRush to create banned.log file
        open FILE,">>$exception_file" or die "Unable to open file!\n";
        print FILE "$info[2]\n";
   close FILE;
    }
}

```

---

### Post by Mithrilhall on 2008-01-24
You might also want to setup fail2ban.

[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

---

