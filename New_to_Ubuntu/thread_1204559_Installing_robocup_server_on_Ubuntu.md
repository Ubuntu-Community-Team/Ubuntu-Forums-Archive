---
title: "Installing robocup server on Ubuntu"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by mzeddot on 2009-07-04
Hey

I'm trying to install rcssserver13.0.2 on Ubuntu. I've configured it but when I try to make it I get this error when linking:

```

.
.
.
mv -f .deps/serializeronlinecoachstdv6.Tpo .deps/serializeronlinecoachstdv6.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializeronlinecoachstdv7.o -MD -MP -MF .deps/serializeronlinecoachstdv7.Tpo -c -o serializeronlinecoachstdv7.o serializeronlinecoachstdv7.cpp
mv -f .deps/serializeronlinecoachstdv7.Tpo .deps/serializeronlinecoachstdv7.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializeronlinecoachstdv8.o -MD -MP -MF .deps/serializeronlinecoachstdv8.Tpo -c -o serializeronlinecoachstdv8.o serializeronlinecoachstdv8.cpp
mv -f .deps/serializeronlinecoachstdv8.Tpo .deps/serializeronlinecoachstdv8.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializeronlinecoachstdv13.o -MD -MP -MF .deps/serializeronlinecoachstdv13.Tpo -c -o serializeronlinecoachstdv13.o serializeronlinecoachstdv13.cpp
mv -f .deps/serializeronlinecoachstdv13.Tpo .deps/serializeronlinecoachstdv13.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializerplayerstdv1.o -MD -MP -MF .deps/serializerplayerstdv1.Tpo -c -o serializerplayerstdv1.o serializerplayerstdv1.cpp
mv -f .deps/serializerplayerstdv1.Tpo .deps/serializerplayerstdv1.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializerplayerstdv7.o -MD -MP -MF .deps/serializerplayerstdv7.Tpo -c -o serializerplayerstdv7.o serializerplayerstdv7.cpp
mv -f .deps/serializerplayerstdv7.Tpo .deps/serializerplayerstdv7.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializerplayerstdv8.o -MD -MP -MF .deps/serializerplayerstdv8.Tpo -c -o serializerplayerstdv8.o serializerplayerstdv8.cpp
mv -f .deps/serializerplayerstdv8.Tpo .deps/serializerplayerstdv8.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serializerplayerstdv13.o -MD -MP -MF .deps/serializerplayerstdv13.Tpo -c -o serializerplayerstdv13.o serializerplayerstdv13.cpp
mv -f .deps/serializerplayerstdv13.Tpo .deps/serializerplayerstdv13.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT serverparam.o -MD -MP -MF .deps/serverparam.Tpo -c -o serverparam.o serverparam.cpp
mv -f .deps/serverparam.Tpo .deps/serverparam.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT stdoutsaver.o -MD -MP -MF .deps/stdoutsaver.Tpo -c -o stdoutsaver.o stdoutsaver.cpp
mv -f .deps/stdoutsaver.Tpo .deps/stdoutsaver.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT stdtimer.o -MD -MP -MF .deps/stdtimer.Tpo -c -o stdtimer.o stdtimer.cpp
mv -f .deps/stdtimer.Tpo .deps/stdtimer.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT synctimer.o -MD -MP -MF .deps/synctimer.Tpo -c -o synctimer.o synctimer.cpp
mv -f .deps/synctimer.Tpo .deps/synctimer.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT team.o -MD -MP -MF .deps/team.Tpo -c -o team.o team.cpp
mv -f .deps/team.Tpo .deps/team.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT timer.o -MD -MP -MF .deps/timer.Tpo -c -o timer.o timer.cpp
mv -f .deps/timer.Tpo .deps/timer.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT utility.o -MD -MP -MF .deps/utility.Tpo -c -o utility.o utility.cpp
mv -f .deps/utility.Tpo .deps/utility.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT visualsendercoach.o -MD -MP -MF .deps/visualsendercoach.Tpo -c -o visualsendercoach.o visualsendercoach.cpp
mv -f .deps/visualsendercoach.Tpo .deps/visualsendercoach.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT visualsenderplayer.o -MD -MP -MF .deps/visualsenderplayer.Tpo -c -o visualsenderplayer.o visualsenderplayer.cpp
mv -f .deps/visualsenderplayer.Tpo .deps/visualsenderplayer.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT xmlreader.o -MD -MP -MF .deps/xmlreader.Tpo -c -o xmlreader.o xmlreader.cpp
mv -f .deps/xmlreader.Tpo .deps/xmlreader.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT xpmholder.o -MD -MP -MF .deps/xpmholder.Tpo -c -o xpmholder.o xpmholder.cpp
mv -f .deps/xpmholder.Tpo .deps/xpmholder.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT player_command_parser.o -MD -MP -MF .deps/player_command_parser.Tpo -c -o player_command_parser.o player_command_parser.cpp
mv -f .deps/player_command_parser.Tpo .deps/player_command_parser.Po
g++ -DHAVE_CONFIG_H -I. -I..  -I.. -I/usr/include -W -Wall -g -O2 -MT player_command_tok.o -MD -MP -MF .deps/player_command_tok.Tpo -c -o player_command_tok.o player_command_tok.cpp
mv -f .deps/player_command_tok.Tpo .deps/player_command_tok.Po
/bin/bash ../libtool --tag=CXX   --mode=link g++ -W -Wall -g -O2 -L../rcssbase/conf -L../rcssbase/net -L../rcssbase/gzip -L/usr/lib -o rcssserver audio.o bodysender.o coach.o csvsaver.o dispsender.o field.o fullstatesender.o heteroplayer.o initsender.o initsendercoach.o initsenderlogger.o initsendermonitor.o initsenderonlinecoach.o initsenderplayer.o landmarkreader.o logger.o main.o monitor.o netif.o pcombuilder.o pcomparser.o player.o playerparam.o object.o referee.o remoteclient.o resultsaver.o serializer.o serializercoachstdv1.o serializercoachstdv7.o serializercoachstdv8.o serializercoachstdv13.o serializercommonstdv1.o serializercommonstdv7.o serializercommonstdv8.o serializermonitor.o serializeronlinecoachstdv1.o serializeronlinecoachstdv6.o serializeronlinecoachstdv7.o serializeronlinecoachstdv8.o serializeronlinecoachstdv13.o serializerplayerstdv1.o serializerplayerstdv7.o serializerplayerstdv8.o serializerplayerstdv13.o serverparam.o stdoutsaver.o stdtimer.o synctimer.o team.o timer.o utility.o visualsendercoach.o visualsenderplayer.o xmlreader.o xpmholder.o player_command_parser.o player_command_tok.o -lrcssclangparser -lrcssconfparser -lrcssnet -lrcssgz   -lz -lm 
g++ -W -Wall -g -O2 -o .libs/rcssserver audio.o bodysender.o coach.o csvsaver.o dispsender.o field.o fullstatesender.o heteroplayer.o initsender.o initsendercoach.o initsenderlogger.o initsendermonitor.o initsenderonlinecoach.o initsenderplayer.o landmarkreader.o logger.o main.o monitor.o netif.o pcombuilder.o pcomparser.o player.o playerparam.o object.o referee.o remoteclient.o resultsaver.o serializer.o serializercoachstdv1.o serializercoachstdv7.o serializercoachstdv8.o serializercoachstdv13.o serializercommonstdv1.o serializercommonstdv7.o serializercommonstdv8.o serializermonitor.o serializeronlinecoachstdv1.o serializeronlinecoachstdv6.o serializeronlinecoachstdv7.o serializeronlinecoachstdv8.o serializeronlinecoachstdv13.o serializerplayerstdv1.o serializerplayerstdv7.o serializerplayerstdv8.o serializerplayerstdv13.o serverparam.o stdoutsaver.o stdtimer.o synctimer.o team.o timer.o utility.o visualsendercoach.o visualsenderplayer.o xmlreader.o xpmholder.o player_command_parser.o player_command_tok.o  -L/home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/conf -L/home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/net -L/home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/gzip -L/usr/lib /home/zeddot/Desktop/rcssserver-13.0.2/src/.libs/librcssclangparser.so /home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/conf/.libs/librcssconfparser.so /home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/net/.libs/librcssnet.so /home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/gzip/.libs/librcssgz.so -lz -lm 
csvsaver.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::exists<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:279: undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int&)'
logger.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::is_directory<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:289: undefined reference to `boost::filesystem::detail::status_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int&)'
logger.o: In function `boost::enable_if<boost::filesystem::is_basic_path<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >, bool>::type boost::filesystem::create_directory<boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> >(boost::filesystem::basic_path<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, boost::filesystem::path_traits> const&)':
/usr/include/boost/filesystem/operations.hpp:396: undefined reference to `boost::filesystem::detail::create_directory_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/home/zeddot/Desktop/rcssserver-13.0.2/rcssbase/conf/.libs/librcssconfparser.so: undefined reference to `boost::filesystem::detail::get_current_path_api(std::basic_string<char, std::char_traits<char>, std::allocator<char> >&)'
collect2: ld returned 1 exit status
make[3]: *** [rcssserver] Error 1
make[3]: Leaving directory `/home/zeddot/Desktop/rcssserver-13.0.2/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/zeddot/Desktop/rcssserver-13.0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zeddot/Desktop/rcssserver-13.0.2'
make: *** [all] Error 2


```

Any suggestions to fix this? 

Cheers
Moin

---

### Post by mzeddot on 2009-07-04
LOL. I fixed it myself. Delete this thread please.

---

### Post by amgmagician on 2009-07-18
May you tell us how can you fix it?

---

