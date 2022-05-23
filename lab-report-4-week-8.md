# Markdown File Review
- - -
> Overview: Review two Markdown parse.
 3 implementations were made to each file to discover issues.

Repo links to the MarkdownParse files:

[MarkdownParse 1](https://github.com/taixinw/markdown-parser)

[MarkdownParse 2](https://github.com/richmass1/markdown-parser)

- - - 
### Snippet 1

This implementaion should produce the following result
![snnipet1](snnipet1.png)

the test was written in the MarkdownTest file
```
    @Test
    public void testsnippet1() throws IOException {
        String contents = Files.readString(Path.of("C:/Users/taixin/Documents/GitHub/markdown-parser/snippet1.md"));
        List<String> expect = List.of("url.com","`google.com","google.com","ucsd.edu");
        assertEquals(expect,MarkdownParse.getLinks(contents));
    }

```
**Test Output**
#### MarkdownParse 1 - Mine
![output1](s1output.png)


I have nerver consider the senerio where brackets could be inside of name of the link. To fix this issue bigger change of code is needed. A loop is needed to search for the last close bracket. After the index of the last close bracket is located, the program can verify if open parenthesis is on the next index.

- - -
### Snippet 2
This implementaion should produce the following result
![snnipet2](snnipet2.png)

the test was written in the MarkdownTest file
```
    @Test
    public void testsnippet2() throws IOException {
        String contents = Files.readString(Path.of("C:/Users/taixin/Documents/GitHub/markdown-parser/snippet2.md"));
        List<String> expect = List.of("a.com","b.com","a.com(())","example.com");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }

```
**Test Output**

#### MarkdownParse 1 - Mine
![output2](s2output.png)

To fix this bug, a small change of code is needed. I have never consider parenthesis can be inside the link. After the open parenthesis is loacted, the propgram should search for the las parenthesis and return the text inbewteen them.
- - - 
### Snippet 3
This implementaion should produce the following result
![snnipet3](snnipet3.png)

the test was written in the MarkdownTest file
```
    @Test
    public void testsnippet3() throws IOException {
        String contents = Files.readString(Path.of("C:/Users/taixin/Documents/GitHub/markdown-parser/snippet3.md"));
        List<String> expect = List.of(" https://www.twitter.com","https://ucsd-cse15l-w22.github.io","github.com","https://cse.ucsd.edu/");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }

```
**Test Output**

#### MarkdownParse 1 - Mine
![output3](s3output.png)

To fix this bug, a big change of code is required. Beacuse there is a link inside another link, which is a scenrio that was never considered before.
