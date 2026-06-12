---
title: "Help with mod_perl migration"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by gupta_sumesh63 on 2011-08-31
I have downloaded the following mod_perl file. It is probably in mod_perl1.0. I wish to use it in mod_perl2.0.

any help in re-engineering the code for using in mod_perl2.0 will be highly appreciated. Moreover what config is to be added to apache2.conf to run it.
Thanks in advance

Sumesh

[PHP]package BookDetail;
# file: BookDetail.pm

use strict;
use Apache::Constants ':common';
use Apache::Request;

####
#
# top_html()
#
# a subroutine that will return the HTML for the top of
# the page - this will create a look and feel like the
# rest of the website
#
####

sub top_html {
    return <<EOHTML;
<html>
<head>
<title>Open Source Web Book - Book Detail Information</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
 
<body bgcolor="#FFFFFF" text="#333333" leftmargin="0" topmargin="0"
marginwidth="0" marginheight="0" link="#333333">
<table width="780" border="0" cellspacing="0" cellpadding="0">
<tr>
<td bgcolor="#000000" colspan="3" align="center"><font color="#FFFFFF">
www.opensourcewebbook.com
</font></td>
</tr>
<tr>
<td bgcolor="#999966" colspan="3">&nbsp;</td>
</tr>
<tr>
<td width="15">&nbsp;</td>
<td width="180">&nbsp;</td>
<td>&nbsp;</td>
</tr>
</table>
<table width="780" border="0" cellspacing="0" cellpadding="0">
<tr>
<td width="15">&nbsp;</td>
<td width="570"><font color="#FF0000"><b>Page Path -</b></font> 
<a href="/contents/"><font color="#999966"><b>Contents</b></font></a> -
<a href="/contents/mod_perl/"><font
color="#999966"><b>mod_perl</b></font></a> -
<a href="/bookdetail/"><font color="#999966"><b>/bookdetail/</b></font></a>
</td>
<td width="195">
<div align="center"><img src="/icons/logo.gif" width="177"
height="51"></div>
</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
</table>
<table width="780" border="0" cellspacing="0" cellpadding="0">
<tr>
<td width="15">&nbsp;</td>
<td width="168" valign="top">
 
 
<table width="164" cellspacing="3" cellpadding="0">
<tr><td><a href="/"><font color="#999966"><b>Home</b></font></a></td></tr>
<tr><td><a href="/about/"><font 
color="#999966"><b>About</b></font></a></td></tr>
<tr><td><a href="/foreword/"><font
color="#999966"><b>Foreword</b></font></a></td></tr>
<tr><td><a href="/reviews/"><font
color="#999966"><b>Reviews</b></font></a></td></tr>
<tr><td><a href="/authors/"><font
color="#999966"><b>Authors</b></font></a></td></tr>
<tr><td><a href="/purchase/"><font
color="#999966"><b>Purchase</b></font></a></td></tr>
<tr><td><a href="/errata/"><font
color="#999966"><b>Errata</b></font></a></td></tr>
<tr><td><a href="/sourcecode/"><font
color="#999966"><b>Sourcecode</b></font></a></td></tr>
<tr><td><a href="/resources/"><font
color="#999966"><b>Resources</b></font></a></td></tr>
<tr><td><a href="/tools/"><font
color="#999966"><b>Tools</b></font></a></td></tr>
<tr><td><a href="/contents/"><font
color="#999966"><b>Contents</b></font></a></td></tr>
<tr><td>
  <table width="130" cellspacing="3" cellpadding="0" align="right">
    <tr><td><a href="/contents/linux/"><font
color="#999966"><b>Linux</b></font></a></td></tr>
    <tr><td><a href="/contents/apache/"><font
color="#999966"><b>Apache</b></font></a></td></tr>
    <tr><td><a href="/contents/perl/"><font
color="#999966"><b>Perl</b></font></a></td></tr>
    <tr><td><a href="/contents/mysql/"><font
color="#999966"><b>MySQL</b></font></a></td></tr>
    <tr><td><a href="/contents/wml/"><font
color="#999966"><b>WML</b></font></a></td></tr>
    <tr><td><a href="/contents/cgi/"><font color="#999966"><b>CGI
</b></font></a></td></tr>
    <tr><td><a href="/contents/mod_perl/"><font
color="#999966"><b>mod_perl</b></font></a></td></tr>
    <tr><td><a href="/contents/ssi/"><font
color="#999966"><b>SSI</b></font></a></td></tr>
    <tr><td><a href="/contents/embperl/"><font
color="#999966"><b>Embperl</b></font></a></td></tr>
    <tr><td><a href="/contents/mason/"><font
color="#999966"><b>Mason</b></font></a></td></tr>
    <tr><td><a href="/contents/php/"><font
color="#999966"><b>PHP</b></font></a></td></tr>
  </table>
</td></tr>
</table>
</td>
<td width="10">&nbsp;</td>
<td width="2" bgcolor="#999966">&nbsp;</td>
<td width="20">&nbsp;</td>
<td width="500" valign="top">
<p><font color="#FF0000"><b>Book Detail Information Built with
mod_perl</b></font><br></p>
<hr>
<p>&nbsp;</p>
EOHTML
}

####
#
# end of top_html()
#
####
 
####
#
# bottom_html()
#
# a subroutine that will return the HTML for the bottom of
# the page 
#
####

sub bottom_html {
    return <<EOHTML;
</td>
<td width="65">&nbsp;</td>
</tr>
</table>
</body>
</html>
EOHTML
}

####
#
# end of bottom_html()
#
####
 
####
#
# handler()
#
####

sub handler {
    # shift the argument and pass it into
    # the new() method in the Apache::Request
    # class
    my $r = new Apache::Request(shift);

    # retrieve the ISBN for which we will
    # show the book detail information
    my $isbn = $r->param('isbn') || 0;

    # set the content type and send the header
    $r->content_type('text/html');
    $r->send_http_header();

    # open the data file - if the open() fails
    # and returns false, print an error message
    # to the browser and return OK
    unless (open FH, '/var/www/misc/book_data.txt') { 
        $r->print(<<EOHTML);
<html>
<head>
<title>Book Detail Information Error</title>
</head>
<body bgcolor="#ffffff">
<h1>Error</h1>
Opening of /var/www/misc/book_data.txt failed.
</body>
</html>
EOHTML

        return OK;
    }

    # print the initial HTML
    $r->print(top_html());

    # set a flag indicated whether or not we have found
    # our record
    my $found = 0;

    # declare some variables to be used in the following
    # while loop
    my($book_isbn, $author, $title, $publisher, 
       $date, $desc, $price);
    my($book);

    # loop through the file book_data.txt, removing
    # the newline, and then splitting the line on a \t,
    # then compare if the ISBN in the record matches
    # the one requested - if so, set $found to 1
    while ($book = <FH>) {
        chomp($book);
	(
            $book_isbn,
            $author,
            $title,
            $publisher,
            $date,
            $desc,
            $price
        ) = split /\t/, $book;
	if ($isbn eq $book_isbn) {
	    $found = 1;
	    last;
	}
    }

    # close the data file
    close FH;

    # if $found is 1, we found our book, and our variables
    # were set, so print them out - if $found is 0, then
    # tell the user the ISBN was not found
    if ($found) {
	$r->print(<<EOHTML);
<table align="center">
<tr><th align="left">ISBN</th><td>$isbn</td></tr>
<tr><th align="left" valign="top">Author</th><td>$author</td></tr>
<tr><th align="left" valign="top">Title</th><td><i>$title</i></td></tr>
<tr><th align="left" valign="top">Publisher</th><td>$publisher</td></tr>
<tr><th align="left">Date</th><td>$date</td></tr>
<tr><th align="left" valign="top">Description</th><td>$desc</td></tr>
<tr><th align="left">Price</th><td>$price</td></tr>
</table>
<p>&nbsp;</p>
<hr>
Click 
<a href="/booklisting/"><font color="#999966"><b>here</b></font></a> 
to find another book.
EOHTML
    } else {
	$r->print("ISBN $isbn not found...\n");
    }

    # finish the HTML and return OK
    $r->print(bottom_html());

    return OK;
}

1;[/PHP]

---

