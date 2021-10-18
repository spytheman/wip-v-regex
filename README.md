# Obsoleted by https://github.com/vlang/pcre

2021/10/18 - Please use the official `pcre` module, by `v install pcre`, then
updating your code to do `import pcre` instead of `import spytheman.regex` .

The API is the same, but the official one is supported, unlike this module.

# v-regex

A simple regex library for [VLang](https://github.com/vlang/v).
It wraps the venerable [PCRE](https://www.pcre.org/) library, so 
you will need it installed as well.

## Prerequisites:

You can install libpcre using your favourite package manager:

Debian: apt-get install libpcre3-dev

Fedora: yum install pcre-devel


## Installation

You can install this module using `v install spytheman.regex`, and
then use it with `import spytheman.regex` .

When there are updates, you can update with `v update spytheman.regex` .

You can also just run `v install spytheman.regex` again.


## Example
(this can also be found in [examples/match_after.v](https://github.com/spytheman/v-regex/blob/master/examples/match_after.v))
```v
import spytheman.regex

fn main() {
  r := regex.new_regex('Match everything after this: (.+)', 0) or {
    println('An error occured!')
    return
  }

  m := r.match_str('Match everything after this: "I <3 VLang!"', 0, 0) or {
    println('No match!')
    return
  }

  // m.get(0) -> Match everything after this: "I <3 VLang!"
  // m.get(1) -> "I <3 VLang!"'
  // m.get(2) -> Error!
  whole_match := m.get(0) or {
    println('We matched nothing...')
    return
  }

  matched_str := m.get(1) or {
    println('We matched nothing...')
    return
  }

  println(whole_match) // Match everything after this: "I <3 VLang!"
  println(matched_str) // "I <3 VLang!"

  r.free()
}
```

```bash
$ v -o example examples/match_after.v
$ ./example
Match everything after this: "I <3 VLang!"
"I <3 VLang!"
```

## Usage

Some examples are available in the [examples](examples/) directory.

## Built With

* [PCRE](https://www.pcre.org/) - Perl Compatible Regular Expressions
* [Vlang](https://github.com/vlang/v) - Simple, fast, safe, compiled language

## License

[MIT](LICENSE)

## Contributors

* [Shellbear](https://github.com/shellbear) - creator
* [Spytheman](https://github.com/spytheman) - maintainer
