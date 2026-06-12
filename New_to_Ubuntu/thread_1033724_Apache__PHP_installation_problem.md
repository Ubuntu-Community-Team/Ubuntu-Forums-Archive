---
title: "Apache / PHP installation problem"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by joshglock on 2009-01-07
I am trying to install Apache 2.2.11 and PHP 5.2.8 and got Apache compiled and installed fine, but I suspect there is so problem in the configuration of the PHP source. Probably something dumb like a missing package but it's still greek to me. Here's the output.

```

josh@mrcomputer:~/Desktop/php-5.2.8$ ./configure --with-mysql --with-apxs=/www/bin/apxs --with-apxs2=/www/bin/apxs
loading cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for icc... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking for system library directory... lib
checking whether to enable runpaths... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... bison -y
checking for bison version... 2.3 (ok)
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for working const... yes
checking for flex version... invalid
configure: warning: flex versions supported for regeneration of the Zend/PHP parsers: 2.5.4  (found: 2.5.35)
checking for re2c... no
configure: warning: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking whether to force non-PIC code in shared modules... yes
checking whether /dev/urandom exists... yes
checking for pthreads_cflags... -pthread
checking for pthreads_lib... 

Configuring SAPI modules
checking for AOLserver support... no
checking for Apache 1.x module support via DSO through APXS... configure: error: You have enabled Apache 1.3 support while your server is Apache 2.  Please use the appropiate switch --with-apxs2
josh@mrcomputer:~/Desktop/php-5.2.8$ ./configure --with-mysql --with-apxs2=/www/bin/apxs
loading cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for icc... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking for system library directory... lib
checking whether to enable runpaths... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... bison -y
checking for bison version... 2.3 (ok)
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for working const... yes
checking for flex version... invalid
configure: warning: flex versions supported for regeneration of the Zend/PHP parsers: 2.5.4  (found: 2.5.35)
checking for re2c... no
configure: warning: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking whether to force non-PIC code in shared modules... yes
checking whether /dev/urandom exists... yes
checking for pthreads_cflags... -pthread
checking for pthreads_lib... 

Configuring SAPI modules
checking for AOLserver support... no
checking for Apache 1.x module support via DSO through APXS... no
checking for Apache 1.x module support... no
checking whether to enable Apache charset compatibility option... no
checking for Apache 2.0 filter-module support via DSO through APXS... no
checking for Apache 2.0 handler-module support via DSO through APXS... yes
checking for Apache 1.x (hooks) module support via DSO through APXS... no
checking for Apache 1.x (hooks) module support... no
checking whether to enable Apache charset compatibility option... no
checking for Caudium support... no
checking for CLI build... yes
checking for Continuity support... no
checking for embedded SAPI library support... no
checking for Zeus ISAPI support... no
checking for Milter support... no
checking for NSAPI support... no
checking for PHTTPD support... no
checking for Pi3Web support... no
checking whether Roxen module is build using ZTS... no
checking for Roxen/Pike support... 
checking for thttpd... no
checking for TUX... no
checking for webjames... no
checking for chosen SAPI module... apache2handler

Running system checks
checking for sendmail... no
checking whether system uses EBCDIC... no
checking whether byte ordering is bigendian... no
checking whether writing to stdout works... This is the test message -- yes
checking for socket... yes
checking for socketpair... yes
checking for htonl... yes
checking for gethostname... yes
checking for gethostbyaddr... yes
checking for yp_get_default_domain... no
checking for __yp_get_default_domain... no
checking for yp_get_default_domain in -lnsl... yes
checking for dlopen... no
checking for __dlopen... no
checking for dlopen in -ldl... yes
checking for sin in -lm... yes
checking for res_search... no
checking for __res_search... no
checking for res_search in -lresolv... yes
checking for inet_aton... yes
checking for dn_skipname... no
checking for __dn_skipname... yes
checking for ANSI C header files... yes
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for inttypes.h... yes
checking for stdint.h... yes
checking for dirent.h... yes
checking for ApplicationServices/ApplicationServices.h... no
checking for sys/param.h... yes
checking for sys/types.h... yes
checking for sys/time.h... yes
checking for netinet/in.h... yes
checking for alloca.h... yes
checking for arpa/inet.h... yes
checking for arpa/nameser.h... yes
checking for assert.h... yes
checking for crypt.h... yes
checking for fcntl.h... yes
checking for grp.h... yes
checking for ieeefp.h... no
checking for langinfo.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for monetary.h... yes
checking for netdb.h... yes
checking for pwd.h... yes
checking for resolv.h... yes
checking for signal.h... yes
checking for stdarg.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for syslog.h... yes
checking for sysexits.h... yes
checking for sys/ioctl.h... yes
checking for sys/file.h... yes
checking for sys/mman.h... yes
checking for sys/mount.h... yes
checking for sys/poll.h... yes
checking for sys/resource.h... yes
checking for sys/select.h... yes
checking for sys/socket.h... yes
checking for sys/stat.h... yes
checking for sys/statfs.h... yes
checking for sys/statvfs.h... yes
checking for sys/vfs.h... yes
checking for sys/sysexits.h... no
checking for sys/varargs.h... no
checking for sys/wait.h... yes
checking for sys/loadavg.h... no
checking for termios.h... yes
checking for unistd.h... yes
checking for unix.h... no
checking for utime.h... yes
checking for sys/utsname.h... yes
checking for sys/ipc.h... yes
checking for dlfcn.h... yes
checking for assert.h... (cached) yes
checking for mach-o/dyld.h... no
checking for fopencookie... yes
checking for broken getcwd... no
checking for broken libc stdio... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tm_zone in struct tm... yes
checking for missing declarations of reentrant functions... done
checking for fclose declaration... ok
checking for tm_gmtoff in struct tm... yes
checking for struct flock... yes
checking for socklen_t... yes
checking size of size_t... 4
checking size of long long... 8
checking size of long long int... 8
checking size of long... 4
checking size of int... 4
checking size of intmax_t... 8
checking size of ssize_t... 4
checking size of ptrdiff_t... 4
checking for st_blksize in struct stat... yes
checking for st_blocks in struct stat... yes
checking for st_rdev in struct stat... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for struct sockaddr_storage... yes
checking for field sa_len in struct sockaddr... no
checking for IPv6 support... yes
checking for vprintf... yes
checking for alphasort... yes
checking for asctime_r... yes
checking for chroot... yes
checking for ctime_r... yes
checking for cuserid... yes
checking for crypt... no
checking for flock... yes
checking for ftok... yes
checking for funopen... no
checking for gai_strerror... yes
checking for gcvt... yes
checking for getloadavg... yes
checking for getlogin... yes
checking for getprotobyname... yes
checking for getprotobynumber... yes
checking for getservbyname... yes
checking for getservbyport... yes
checking for getrusage... yes
checking for gettimeofday... yes
checking for gmtime_r... yes
checking for getpwnam_r... yes
checking for getgrnam_r... yes
checking for getpwuid_r... yes
checking for grantpt... yes
checking for inet_ntoa... yes
checking for inet_ntop... yes
checking for inet_pton... yes
checking for isascii... yes
checking for link... yes
checking for localtime_r... yes
checking for lockf... yes
checking for lchown... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
checking for mkstemp... yes
checking for mmap... yes
checking for nl_langinfo... yes
checking for perror... yes
checking for poll... yes
checking for ptsname... yes
checking for putenv... yes
checking for realpath... yes
checking for random... yes
checking for rand_r... yes
checking for regcomp... yes
checking for res_search... (cached) yes
checking for scandir... yes
checking for setitimer... yes
checking for setlocale... yes
checking for localeconv... yes
checking for setenv... yes
checking for setpgid... yes
checking for setsockopt... yes
checking for setvbuf... yes
checking for shutdown... yes
checking for sin... yes
checking for snprintf... yes
checking for srand48... yes
checking for srandom... yes
checking for statfs... yes
checking for statvfs... yes
checking for std_syslog... no
checking for strcasecmp... yes
checking for strcoll... yes
checking for strdup... yes
checking for strerror... yes
checking for strftime... yes
checking for strptime... yes
checking for strstr... yes
checking for strtok_r... yes
checking for symlink... yes
checking for tempnam... yes
checking for tzset... yes
checking for unlockpt... yes
checking for unsetenv... yes
checking for usleep... yes
checking for nanosleep... yes
checking for utime... yes
checking for vsnprintf... yes
checking for getaddrinfo... yes
checking for strlcat... no
checking for strlcpy... no
checking for getopt... yes
checking whether utime accepts a null argument... yes
checking for working alloca.h... (cached) yes
checking for alloca... yes
checking for declared timezone... yes
checking for type of reentrant time-related functions... POSIX
checking for readdir_r... yes
checking for type of readdir_r... POSIX
checking for in_addr_t... yes
checking for crypt_r... no

General settings
checking whether to include gcov symbols... no
checking whether to include debugging symbols... no
checking layout of installed files... PHP
checking path to configuration file... DEFAULT
checking where to scan for configuration files... 
checking whether to enable safe mode by default... no
checking for safe mode exec dir... /usr/local/php/bin
checking whether to enable PHP's own SIGCHLD handler... no
checking whether to enable magic quotes by default... no
checking whether to explicitly link against libgcc... no
checking whether to enable short tags by default... yes
checking whether to enable dmalloc... no
checking whether to enable IPv6 support... yes
checking how big to make fd sets... using system default

Configuring extensions
checking whether to enable LIBXML support... yes
checking libxml2 install dir... no
checking for xml2-config path... /usr/bin/xml2-config
checking whether libxml build works... yes
checking for OpenSSL support... no
checking for Kerberos support... no
checking for PCRE library to use... bundled
checking for ZLIB support... no
checking if the location of ZLIB install directory is defined... no
checking whether to enable bc style precision math functions... no
checking for BZip2 support... no
checking whether to enable calendar conversion support... no
checking whether to enable ctype functions... yes
checking for cURL support... no
checking if we should use cURL for url streams... no
checking size of long... (cached) 4
checking size of int... (cached) 4
checking for int32_t... yes
checking for uint32_t... yes
checking for sys/types.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for string.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for strtoll... yes
checking for atoll... yes
checking for strftime... (cached) yes
checking for QDBM support... no
checking for GDBM support... no
checking for NDBM support... no
checking for Berkeley DB4 support... no
checking for Berkeley DB3 support... no
checking for Berkeley DB2 support... no
checking for DB1 support... no
checking for DBM support... no
checking for CDB support... no
checking for INI File support... no
checking for FlatFile support... no
checking whether to enable DBA interface... no
checking whether to enable dbase support... no
checking whether to enable DOM support... yes
checking for xml2-config path... (cached) /usr/bin/xml2-config
checking whether libxml build works... (cached) yes
checking whether to enable EXIF (metadata from images) support... no
checking for FrontBase SQL92 (fbsql) support... no
checking for FDF support... no
checking whether to enable input filter support... yes
checking pcre install prefix... no
checking whether to enable FTP support... no
checking OpenSSL dir for FTP... no
checking for GD support... no
checking for the location of libjpeg... no
checking for the location of libpng... no
checking for the location of libXpm... no
checking for FreeType 1.x support... no
checking for FreeType 2... no
checking for T1lib support... no
checking whether to enable truetype string function in GD... no
checking whether to enable JIS-mapped Japanese font support in GD... no
checking for GNU gettext support... no
checking for GNU MP support... no
checking whether to enable hash support... yes
checking whether byte ordering is bigendian... (cached) no
checking size of short... 2
checking size of int... (cached) 4
checking size of long... (cached) 4
checking size of long long... (cached) 8
checking for iconv support... yes
checking for iconv... yes
checking if iconv is glibc's... yes
checking if iconv supports errno... yes
checking if your cpp allows macro usage in include lines... yes
checking for IMAP support... no
checking for IMAP Kerberos support... no
checking for IMAP SSL support... no
checking for InterBase support... no
checking whether to enable JavaScript Object Serialization support... yes
checking for ANSI C header files... (cached) yes
checking for LDAP support... no
checking for LDAP Cyrus SASL support... no
checking whether to enable multibyte string support... no
checking whether to enable multibyte regex support... yes
checking whether to check multibyte regex backtrack... yes
checking for external libmbfl... no
checking for mcrypt support... no
checking for mhash support... no
checking whether to include mime_magic support... no
checking for MING support... no
checking for mSQL support... no
checking for MSSQL support via FreeTDS... no
checking for MySQL support... yes
checking for specified location of the MySQL UNIX socket... no
checking for MySQL UNIX socket location... no
configure: error: Cannot find MySQL header files under yes.
Note that the MySQL client library is not bundled anymore!
josh@mrcomputer:~/Desktop/php-5.2.8$ make
make: *** No targets specified and no makefile found.  Stop.


```

Any help is much appreciated. Thanks in advance!

---

### Post by blueridgedog on 2009-01-07
Have you tried installing the modules you want via apt-get?

```
sudo apt-get install apache2 php5 libapache2-mod-php5

sudo apt-get install mysql-server mysql-client php5-mysql
```

---

### Post by mcduck on 2009-01-07
Unless you have some special reason to compile that stuff from source code, the easiest way to get everything is to run this command:

```
sudo tasksel install lamp-server
```

It will install and configure Apache2, PHP and MySQL for you.

---

### Post by joshglock on 2009-01-07
Thanks everybody! I got apache up and running, but when I attempt to load up a php located in /var/www (ex. [http://127.0.0.1/test.php](http://127.0.0.1/test.php) that I created using gedit) Firefox just pops trying to save the file to my computer. I ran the 3 commands that were posted above, so that's where I'm at now.

I'll probably continue to play around trying to figure it out, but I have a feeling that somebody else can tell me exactly what I need to do before I can figure it out and possibly mess it up.

I have a feeling that PHP just isn't installed?

Thanks again,
Josh

---

### Post by Iowan on 2009-01-07
I'm a li'l over my head here... My LAMP server has a file **/etc/phpmyadmin/apache.conf** with a section <IfModule mod_php5.c>. The first line in the section is *AddType application/x-http-php .php*  I suspect that tells Apache that .php files are processed - rather than just transmitted.  How/where this file gets included (or otherwise integrated) into Apache??

---

### Post by joshglock on 2009-01-08
I figured it out, all I had to do was restart my Apache server, doH! 
Just typed in ```
sudo /etc/init.d/apache2 restart
``` and all was well.

---

