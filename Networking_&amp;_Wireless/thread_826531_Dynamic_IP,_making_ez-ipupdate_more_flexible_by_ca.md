---
title: "Dynamic IP, making ez-ipupdate more flexible by calling another program to get IP"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by irwand on 2008-06-12
I recently made a patch to ez-ipupdate so that it will run a program to determine the IP of the server machine. Normally ez-ipupdate gets the machine's IP automatically but only using the local IP of the machine. This doesn't quite work for me since my computer is located behind a NAT router.

Unfortunately, I can't find anyway to contact the maintainer of ez-ipupdate. The email address of the maintainer is no longer valid. I'm hoping that by posting this patch here, other people might find this useful. If you know the current maintainer of ez-ipupdate, please let me know so I can send this patch his/her way.

Here's the patch:

```
diff -aur ez-ipupdate-3.0.11b7/ez-ipupdate.c ez-ipupdate-3.0.11b7+ipcommand/ez-ipupdate.c
--- ez-ipupdate-3.0.11b7/ez-ipupdate.c	2002-03-11 17:31:47.000000000 -0600
+++ ez-ipupdate-3.0.11b7+ipcommand/ez-ipupdate.c	2008-01-03 00:43:22.000000000 -0600
@@ -265,6 +265,7 @@
 int max_interval = 0;
 int service_set = 0;
 char *post_update_cmd = NULL;
+char *get_ip_cmd = NULL;
 char *post_update_cmd_arg = NULL;
 int connection_type = 1;
 time_t last_update = 0;
@@ -547,6 +548,7 @@
   CMD_debug,
   CMD_execute,
   CMD_foreground,
+  CMD_getipcmd,
   CMD_quiet,
   CMD_timeout,
   CMD_run_as_user,
@@ -572,6 +574,7 @@
   { CMD_pid_file,        "pid-file",        CONF_NEED_ARG, 1, conf_handler, "%s=<file>" },
   { CMD_host,            "host",            CONF_NEED_ARG, 1, conf_handler, "%s=<host>" },
   { CMD_interface,       "interface",       CONF_NEED_ARG, 1, conf_handler, "%s=<interface>" },
+  { CMD_getipcmd,        "getipcmd",        CONF_NEED_ARG, 1, conf_handler, "%s=<shell command>" },
   { CMD_mx,              "mx",              CONF_NEED_ARG, 1, conf_handler, "%s=<mail exchanger>" },
   { CMD_max_interval,    "max-interval",    CONF_NEED_ARG, 1, conf_handler, "%s=<number of seconds between updates>" },
   { CMD_notify_email,    "notify-email",    CONF_NEED_ARG, 1, conf_handler, "%s=<address to email if bad things happen>" },
@@ -630,6 +633,7 @@
   fprintf(stdout, "  -g, --request-uri <uri>\tURI to send updates to\n");
   fprintf(stdout, "  -h, --host <host>\t\tstring to send as host parameter\n");
   fprintf(stdout, "  -i, --interface <iface>\twhich interface to use\n");
+  fprintf(stdout, "  -j, --getipcmd <command>\tshell command to print a line IP address to use. This override interface option.\n");
   fprintf(stdout, "  -L, --cloak_title <host>\tsome stupid thing for DHS only\n");
   fprintf(stdout, "  -m, --mx <mail exchange>\tstring to send as your mail exchange\n");
   fprintf(stdout, "  -M, --max-interval <# of sec>\tmax time in between updates\n");
@@ -926,6 +930,19 @@
       dprintf((stderr, "fork()ing off\n"));
       break;
 
+    case CMD_getipcmd:
+#if defined(HAVE_WAITPID) || defined(HAVE_WAIT)
+      if(get_ip_cmd) { free(get_ip_cmd); }
+      get_ip_cmd = malloc(strlen(optarg) + 1 + ARGLENGTH + 1);
+      post_update_cmd_arg = get_ip_cmd + strlen(optarg) + 1;
+      sprintf(get_ip_cmd, "%s ", optarg);
+      dprintf((stderr, "get_ip_cmd: %s\n", get_ip_cmd));
+#else
+      fprintf(stderr, "command execution not enabled at compile time\n");
+      exit(1);
+#endif
+      break;
+
     case CMD_pid_file:
 #if HAVE_GETPID
       if(pid_file) { free(pid_file); }
@@ -1177,6 +1194,7 @@
       {"pid-file",        required_argument,      0, 'F'},
       {"host",            required_argument,      0, 'h'},
       {"interface",       required_argument,      0, 'i'},
+      {"getipcmd",        required_argument,      0, 'j'},
       {"cloak_title",     required_argument,      0, 'L'},
       {"mx",              required_argument,      0, 'm'},
       {"max-interval",    required_argument,      0, 'M'},
@@ -1205,7 +1223,7 @@
 #endif
   int opt;
 
-  while((opt=xgetopt(argc, argv, "a:b:c:dDe:fF:g:h:i:L:m:M:N:o:p:P:qQ:r:R:s:S:t:T:U:u:wHVCZz:", 
+  while((opt=xgetopt(argc, argv, "a:b:c:dDe:fF:g:h:i:j:L:m:M:N:o:p:P:qQ:r:R:s:S:t:T:U:u:wHVCZz:", 
           long_options, NULL)) != -1)
   {
     switch (opt)
@@ -1264,6 +1282,10 @@
         option_handler(CMD_interface, optarg);
         break;
 
+      case 'j':
+        option_handler(CMD_getipcmd, optarg);
+        break;
+
       case 'L':
         option_handler(CMD_cloak_title, optarg);
         break;
@@ -1602,8 +1624,17 @@
   return(bread);
 }
 
+char* get_ip_from_cmd(char *cmd, int* error);
 int get_if_addr(int sock, char *name, struct sockaddr_in *sin)
 {
+  if (strcmp(name, "getipcmd") == 0)
+  {
+    int error;
+    char *ipstr = get_ip_from_cmd(get_ip_cmd, &error);
+    inet_aton(ipstr, &(sin->sin_addr));
+    return error;
+  }
+
 #ifdef IF_LOOKUP
   struct ifreq ifr;
 
@@ -4341,6 +4372,110 @@
 #endif
 }
 
+char* get_ip_from_cmd(char *cmd, int* error)
+{
+  static char newipbuf[64];
+  newipbuf[0]='\0';
+  *error = 0;
+  char *retVal, *tail;
+#if (defined(HAVE_WAITPID) || defined(HAVE_WAIT)) && (defined(HAVE_VFORK) || defined(HAVE_FORK))
+  int kid;
+  int exit_code;
+  int ip_pipe[2];
+
+  pipe(ip_pipe);
+
+  /*
+                  if(res == -1)
+                  {
+                    show_message("(%s) error running post update command: %s\n",
+                        N_STR(host), error_string);
+                  }
+                  else
+                  {
+                    show_message(
+                        "(%s) error running post update command, command exit code: %d\n",
+                        N_STR(host), res);
+                  }
+                  */
+
+  switch((kid=vfork()))
+  {
+    case -1:
+      if(!(options & OPT_QUIET))
+      {
+        perror("fork");
+      }
+      show_message("(%s) error running get_ip_cmd: %s\n",
+          N_STR(host), error_string);
+      *error = -1;
+      return(newipbuf);
+      break;
+    case 0:
+      /* child */
+      close(ip_pipe[0]);
+      close(1);
+      dup2(ip_pipe[1],1);
+      execl("/bin/sh", "sh", "-c", cmd, (char *)0);
+      if(!(options & OPT_QUIET))
+      {
+        perror("exec");
+      }
+      exit(1);
+      break;
+    default:
+      /* parent */
+      dprintf((stderr, "forked kid: %d\n", kid));
+      break;
+  }
+
+#  ifdef HAVE_WAITPID
+  if(waitpid(kid, &exit_code, 0) != kid)
+  {
+    dprintf((stderr, "forked kid: %d\n", kid));
+    close(ip_pipe[0]);
+    close(ip_pipe[1]);
+    *error = -1;
+    return(newipbuf);
+  }
+#  else
+  if(wait(&exit_code) != kid)
+  {
+    close(ip_pipe[0]);
+    close(ip_pipe[1]);
+    *error = -1;
+    return(newipbuf);
+  }
+#  endif
+  exit_code = WEXITSTATUS(exit_code);
+  *error = exit_code;
+
+  read(ip_pipe[0], newipbuf, 64);
+  close(ip_pipe[0]);
+  close(ip_pipe[1]);
+
+  /* cleanup return value string, find the beginning of IP address */
+  newipbuf[63] = '\0'; /* set end condition, just in case */
+  for (retVal = newipbuf; *retVal && (*retVal < '0' || *retVal > '9'); ++retVal) {}
+  /* cleanup return value string, cleanup trailing white space */
+  for (tail = retVal; *tail && ((*tail >= '0' && *tail <= '9') || *tail == '.'); ++tail) {}
+  *tail = '\0';
+
+  if (!is_dotted_quad(retVal))
+    retVal[0]='\0';
+
+  dprintf((stderr, "get_ip_from_cmd, got ip: %s\n", retVal));
+  if (*error != 0)
+  {
+    show_message( "ez-ipupdate: get_ip_from_cmd, got ip: %s, error: %d\n", retVal, *error);
+  }
+
+  return(retVal);
+#else
+  return(-1);
+#endif
+}
+
 void handle_sig(int sig)
 {
 
@@ -4395,7 +4530,7 @@
   mcheck(NULL);
 #endif
 
-  dprintf((stderr, "staring...\n"));
+  dprintf((stderr, "starting...\n"));
 
   program_name = argv[0];
   options = 0;
@@ -4473,6 +4608,12 @@
   request = strdup(request_over_ride == NULL ? service->default_request : request_over_ride);
   dprintf((stderr, "request: %s\n", request));
 
+  if (get_ip_cmd)
+  {
+    if (interface) free(interface);
+    interface = strdup("getipcmd");
+  }
+
   if(service->init != NULL)
   {
     service->init();
@@ -4512,9 +4653,12 @@
     if(!(options & OPT_FOREGROUND))
     {
 #  if HAVE_SYSLOG_H
+      /* If we close these, get_ip_from_cmd() doesn't behave correctly,
+       * because new files opened acts as stdin, stdout, and stderr, screwing
+       * things up.
       close(0);
       close(1);
-      close(2);
+      close(2); */
 #  endif
       if(fork() > 0) { exit(0); } /* parent */
     }

```

Here is what the configuration file looks like:
```
#!/usr/sbin/ez-ipupdate -c
###
###  Default ez-ipupdate configuration file - EDIT WITH CARE
###  Use `dpkg-reconfigure ez-ipupdate' to update the debconf-generated lines.
###

###  The following lines were generated by debconf

service-type=<your-service-type>
#server=(default)
user=<your-user-and-password>
host=<your-host>
#interface=eth0
#wildcard
#mx=(none)
run-as-user=ez-ipupd
cache-file=/var/cache/ez-ipupdate/default-cache
daemon

###  Changes below this line will be preserved on upgrades.

getipcmd=/usr/local/bin/whatsmyip.pl
period=7200

```

The configuration tells ez-ipupdate to execute whatsmyip.pl to get the IP address. This executable must just print out the IP address of the machine on stdout using any method that works for your situation. I suggest if at all possible to not use web-scraping. Instead, try to contact your router and get your real IP address from there. Unfortunately for my situation, my router isn't straightforward, so I resort to web-scraping. The code I use for whatsmyip.pl is as follows:

```
#!/usr/bin/perl -wT
use strict;
use LWP::Simple;

my @checkIPURLs = (
   "http://www.ipchicken.com",
   "http://checkip.dyndns.com",
   "http://ipdetect.dnspark.com",
   "http://www.whatismyip.org",
   "http://ipswift.com",
   "http://www.cmyip.com"
);

my $range = scalar(@checkIPURLs);
my $maxLoop = 10;
my $random_number;
my $url;
my $response;
my $gotit;

do {
   $gotit = 0;
   $random_number = int(rand($range));
   $url = $checkIPURLs[$random_number];

   $response = get($url);

   $response =~ s/<.*?>//gs;
   $response =~ s/.*?([0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}).*/$1/gs;
   $maxLoop--;

   $gotit = 1 if ($response =~ m/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}/);
} while (!$gotit && $maxLoop > 0);

if ($response =~ m/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}/)
{
   print "$response\n";
   exit 0;
}
else
{
   print "\n";
   exit 1;
}

```

That's it. I hope that can help someone.
Thanks

---

### Post by UGA_AA on 2011-09-22
Your post was very helpful. I did not want to rescript the ez-ipupdate code, so I took your perl script and called it from a bash script. I was then able to use the ez-ipupdate -address to plug the result of whatsmyip.pl. Just make sure the comment out the interface in the ez-ipupdate.cfg. Below is my bash.

#! /bin/bash
#! /usr/bin/perl
# dyndns_update.sh
# The script Calls whatsmyip perl script and then creates a tmp script to call
myip=`~/whatsmyip.pl` 
echo "/usr/sbin/ez-ipupdate -c /etc/ez-ipupdate.conf -a $myip"> ~/update_dyndns.tmp
chmod 770 ~/update_dyndns.tmp
~/update_dyndns.tmp
rm ~/update_dyndns.tmp

---

### Post by KMatsumari on 2012-03-18
God this is an old thread, but damn this program could use a new rewrite with a package distro for current use. I have only one question since I am still getting to know all the ins-and-outs of linux: for the patch code, where/how exactly do I apply that change? My first guess was to look at the code in /etc/init.d/ez-ipupdate, but that is only for starting the service and it points to the running code in two locations (one for main, one for daemon), but these are written in full-on ASCII or unicode. so am I supposed to plug in your patch directly into the bin code file, or am I supposed to make a new executable out of the patch work and run it? I am getting lost here.

before anyone gets on this bandwagon (if anyone even replies to a 7-year-old thread) and trolls or flames me, understand that I am not a linux genius (hopefully soon though) and I have been pounding out my server for about 19 hours straight this past day, and this will be the umpteenth time I tried to assemble it and get it connected.

I always wondered why my server kept reporting my private IP address, and the guys over at easydns.com didn't arrive at this conclusion for some off reason.

I did think about just running a simple script every hour or so on another GUI machine in my network that would get the IP address from whatismyip.org and enter that into an instance of ez-ipupdate -a x.x.x.x and the rest of my info that never changes, but I'm kinda short on extra computers ATM. I think I'm gonna call easydns back when they open and let them know what i discovered and see if they have any other suggestions for me.

Note, I am running my server with static ip to my router, and my router is a century-link wifi modem/router combo, so there is no option to place a computer ahead of the first router, otherwise I may have done that for my IP updating. Also my server is placed in the DMZ of my router to allow it to be accessed as my public ip address, i just need to update my easydns dynamic DNS records.

---

### Post by irwand on 2012-03-18
To apply the diff, use the patch command. Google around for "apply diff patch". It should give you better information than what I can do given that I don't patch daily.
I'd suggest make a backup the original ez-ipupdate script before trying to patch it. Once you successfully patch it, you can run it and give it a try. Like you said, it's old, so I don't know if the diff can be applied cleanly or not. I currently use a different network configuration where I no longer need to use the trick here.

Besides using the diff here, another option you should consider is to use dd-wrt capable routers. dd-wrt has an option to update ip on ddns service, like easydns.
[http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)
If you can go that route, it's _much_ easier option.

And I'm no security expert, but I thought it's more secure if you use port-forwarding of specific ports rather than using DMZ. Then only those ports are "open" to the outside world. Also, consider running sshd (if you have it running) to a different non-standard port to avoid other computers trying random login to get in. I had this problem, and apparently it's a common problem.

Good luck!

---

### Post by KMatsumari on 2012-03-18
Thankx irwand, I will give this a shot if the config easydns sends me doesn't prevail.

Unfortunately, my router options are limited because I have to use a century-link router/modem combo device that cannot be altered to have a program run from it (formerly Qwest). The only built-in Dynamic Ip updater that is built-in to the router/modem is dyndns' ddns program but that requires a profile and service contract with dyndns.com, which I am paying easydns for ATM.

Lastly, I am using DMZ instead of port forwarding because my server is an All-in-one, meaning I am using everything but a virtual server in my server, so I need almost all ports open to the world, and I only allow ssl, sasl, or tls with login authentication and lockout/jailkit/fail2ban connections to my server when anything is happening outside of my read-only http retieval. Easier than specifying each range of ports for tcp, then udp, then tcp...etc. too many ports to open, so i opened them all, and denied access to the ones within my server that I will not be using.

Again, thanks for the info, and hopefully your patch wil work for what I need should easydns config fail me.

---

