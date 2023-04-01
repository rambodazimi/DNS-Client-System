# DNS-Client-System
DNS Client System

## Introduction
The internet’s domain name system provides the essential service of mapping between domain names (e.g., mcgill.ca or facebook.com) and IP addresses (e.g., 132.216.177.160 or 31.13.65.1). This makes the internet more human-friendly since we only have to remember domain names and not IP addresses.
When you direct an internet-enabled application to a new site (e.g., you open a new website in your browser, or you send an email to someone at a different domain name), the application needs to resolve the domain name to an IP address before it can contact the server. This is accomplished using the DNS request/response mechanism.

Sockets are the programming mechanism used to implement network applications. If you have previously written an application that reads or writes from a file on disk, then you know you first open a file handle, then read/write using the file handle, and finally close the file handle when you are done. Sockets work in a similar way, but instead of reading/writing to a file on disk, they allow you to read/write to another process (usually running on a different machine).

## Project Description
Write a program using Python sockets that:

• Is invoked from the command line (STDIN);

• Sends a query to the server for the given domain name using a UDP socket;

• Waits for the response to be returned from the server;

• Interprets the response and outputs the result to terminal display (STDOUT).

Your DNS client should be capable of performing the following actions:

• Send queries for A (IP addresses), MX (mail server), and NS (name server) records;

• Interpret responses that contain A records (iPad dresses) and CNAME records (Unaliases);

• Retransmit queries that are lost.

Your client must also handle errors gracefully. In particular, if the response message does not conform to the DNS specification, if it contains fields or entries that cannot be interpreted, or if the client receives a response that does not match the query it sent, then an appropriate error message should be printed to the screen indicating what was unexpected or what went wrong.

You must write the code that constructs a DNS request packet and interprets the DNS response packet. You may not use external DNS libraries or classes in your project (such as net.URL or net.InetAddress).

Your application should be named DnsClient, and it should be invoked at the command line using the following syntax:

java DnsClient [-t timeout] [-r max-retries] [-p port] [-mx|-ns] @server name

where the arguments are defined as follows.
• timeout (optional) gives how long to wait, in seconds, before retransmitting an
unanswered query. Default value: 5.
• max-retries(optional) is the maximum number of times to retransmit an
unanswered query before giving up. Default value: 3.
• port (optional) is the UDP port number of the DNS server. Default value: 53.
• -mx or -ns flags (optional) indicate whether to send a MX (mail server) or NS (name server)
query. At most one of these can be given, and if neither is given then the client should send a
type A (IP address) query.
• server (required) is the IPv4 address of the DNS server, in a.b.c.d. format
• name (required) is the domain name to query for.

For example to query for www.mcgill.ca IP address using the McGill DNS server, enter:
java DnsClient @132.206.85.18 www.mcgill.ca

or to query for the mcgill.ca mail server using Google’s public DNS server with a timeout of 10seconds and at most 2 retries, enter:
java DnsClient –t 10 –r 2 –mx @8.8.8.8 mcgill.ca




