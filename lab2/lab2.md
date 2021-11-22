# Computer Network Study Lab 2

---

- Author:PB19000362 钟书锐
- Time:2021.9.23

## 1. The Basic HTTP GET/response interaction

- The picture of the wireshark.
  ![](./asset/1.1.png)

- The picture of the http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
  ![](./asset/1.2.png)

### Q1 Is your browser running HTTP version 1.0 or 1.1? What version of HTTP is the server running?

Both are HTTP 1.1

### Q2. What languages (if any) does your browser indicate that it can accept to the server?

Accept-Language:

zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6,zh-TW;q=0.5

### Q3. What is the IP address of your computer? Of the gaia.cs.umass.edu server?

- IP address of my computer:192.168.213.57
- IP address of the server:128.119.245.12

### Q4. What is the status code returned from the server to your browser?

200

### Q5. When was the HTML file that you are retrieving last modified at the server?

Last-Modified: Thu, 23 Sep 2021 05:59:02 GMT

### Q6. How many bytes of content are being returned to your browser?

128

### Q7. By inspecting the raw data in the packet content window, do you see any headerswithin the data that are not displayed in the packet-listing window? If so, name one.

No, all of the headers can be found in the raw data.

## 2. The HTTP CONDITIONAL GET/response interaction

- The picture of the wireshark.
  ![](./asset/2.1.png)
- The picture of the http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file2.html
  ![](./asset/2.2.png)

### Q8. Inspect the contents of the first HTTP GET request from your browser to the server. Do you see an “IF-MODIFIED-SINCE” line in the HTTP GET?

No.

### Q9. Inspect the contents of the server response. Did the server explicitly return the contents of the file? How can you tell?

Yes,we can see the contents in the Line-based text data field,and the content-Length is 371.

### Q10. Now inspect the contents of the second HTTP GET request from your browser to the server. Do you see an “IF-MODIFIED-SINCE:” line in the HTTP GET? If so, what information follows the “IF-MODIFIED-SINCE:” header?

- Yes.
- If-Modified-Since: Thu, 23 Sep 2021 05:59:02 GMT\r\n
- This is the date of the last modification of the file from the previous get request.

### Q11. What is the HTTP status code and phrase returned from the server in response to this second HTTP GET? Did the server explicitly return the contents of the file?Explain.

- 304 Not Modified
- No, The server didn’t return the contents of the file since the browser loaded it
  from its cache. Return the contents will just waste time.

## 3. Retrieving Long Documents

- The picture of the wireshark.
  ![](./asset/3.1.png)

- The picture of the http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
  ![](./asset/3.2.png)

### Q12. How many HTTP GET request messages did your browser send? Which packet number in the trace contains the GET message for the Bill or Rights?

- My browser send 1 HTTP GET request message.
- All the 4 packets contains the GET message for the Bill or Rights.(166,167,168,170)

### Q13. Which packet number in the trace contains the status code and phrase associated with the response to the HTTP GET request?

The first packet(166).

### Q14. What is the status code and phrase in the response?

200 OK

### Q15. How many data-containing TCP segments were needed to carry the single HTTP response and the text of the Bill of Rights?

4

## 4.HTML Documents with Embedded Objects

- The picture of the wireshark.
  ![](./asset/4.1.png)

- The picture of the http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
  ![](./asset/4.2.png)

### Q16. How many HTTP GET request messages did your browser send? To which Internet addresses were these GET requests sent?

Browser send 3 request
128.119.245.12
128.119.245.12
178.79.137.164

### Q17. Can you tell whether your browser downloaded the two images serially, orwhether they were downloaded from the two web sites in parallel?Explain

- Serially, see the time.
- The first image (send request at 7.225681,and receive at 7.474334)
- The second image (send request at 8.147958,and receive at 8.481968)

## 5.HTTP Authentication

- The picture of the wireshark.
  ![](./asset/5.1.png)

- The picture before enter the web.
  ![](./asset/5.3.png)

- The picture of the http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file5.html
  ![](./asset/5.2.png)

### Q18. What is the server’s response (status code and phrase) in response to the initial HTTP GET message from your browser?

401 Unauthorized

### Q19. When your browser’s sends the HTTP GET message for the second time, what new field is included in the HTTP GET message?

Authorization: Basic d2lyZXNoYXJrLXN0dWRlbnRzOm5ldHdvcms=\r\n
