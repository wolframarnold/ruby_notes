# Expression values

In Ruby, every expression evaluates to some value

    @@@ ruby
    >> 2 + 2
    => 4
    >> (2+2).zero?
    => false
    >> "zero" if (2+2).zero?
    => nil

# Parameters and return values

    @@@ ruby
    def thing.to_fahrenheit(celcius)
      celcius * 9.0 / 5 + 32
    end

* `celcius` is a parameter
* the value of a function is the value of the final statement
  * in this case, the only statement
* the keyword `return` is available, but usually unnecessary

# Arguments vs. Parameters

* Technically speaking, *arguments* are passed and *parameters* are declared

...

    @@@ ruby
    def thing.to_fahrenheit(celcius)
      celcius * 9.0 / 5 + 32
    end
    boiling = 100
    thing.to_fahrenheit(boiling)

 ...

* Note that the variable names don't have to match!
* In this code, `boiling` is an argument and `celcius` is a parameter
  * In practice, the two terms are interchangeable

# Splat arguments

    @@@ ruby
    def thing.greet(greeting, *names)
      names.each do |name|
        puts "#{greeting}, #{name}!"
      end
    end

    >> thing.greet("Hello", "Alice", "Bob", "Charlie")
    Hello, Alice!
    Hello, Bob!
    Hello, Charlie!

# Default values

    @@@ ruby
    def thing.eat(food = "chicken")
      puts "Yum, #{food}!"
    end

    >> thing.eat
    Yum, chicken!

    >> thing.eat "arugula"
    Yum, arugula!

# The default hash parameter

When calling a method, if the final argument is a hash, you can **leave off** the curly braces

    @@@ ruby
    def print_value_plus(amount, hash)
      hash.each_pair {|k,v| puts v + amount }
    end

    print_value_plus 2, :x => 1, :y => 2
    # same as...
    print_value_plus(2, {:x => 1, :y => 2})