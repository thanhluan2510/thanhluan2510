### Hi there 👋

<!--
**thanhluan2510/thanhluan2510** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on Technical Recruitment
- 🌱 I’m currently learning Technical Skills in IT
- 👯 I’m looking to collaborate on new job opportunity with Developers & Engineers in IT field
- 💬 Ask me about new job opportunites on: Frontend, Backend, Tester, System, Data, Cloud ...
- 📫 How to reach me: Skype: live:37b8f131147b6f48, Linkedin: https://www.linkedin.com/in/luan-vo-%F0%9F%94%A5-a84605194/

-->
const axios = require("axios");
const fs = require("fs");

const getQuote = async () => {
  try {
    const { data } = await axios.get("https://quotes.rest/qod?language=en&quot;);
    const quote = data.contents.quotes[0].quote;
    const author = data.contents.quotes[0].author;

    console.log("new quote", `"${quote}"`);

    return {
      quote,
      author,
    };
  } catch (err) {
    console.error(err.message);
    return {};
  }
};

const generate = async () => {
  const { quote, author } = await getQuote();

  if (!quote) return;

  fs.writeFileSync("README.md", `_**${quote}**_\n\n${author}`);
};

generate();
