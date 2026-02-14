Scraping Method Investigation

Why requests + BeautifulSoup fails

The HTML returned from https://quotes.toscrape.com/js/ does not contain the quotes.
It only contains empty containers and JavaScript files.
Since BeautifulSoup parses only the server HTML response, it cannot extract any quote data.


Network Investigation

Inspection of the Network tab showed no API endpoint returning quote data in JSON format — only HTML, CSS, and JavaScript resources were loaded.
However, the quotes appeared in the DOM after page rendering, indicating the content is generated client-side via JavaScript rather than retrieved through a public API.
Therefore, the data cannot be accessed using requests
Therefore, Selenium was chosen because it renders the page in a real browser and allows extraction of dynamically generated content.


Data Cleaning

The raw dataset was cleaned to ensure consistency and usability before analysis.
The following steps were performed:
Verified and confirmed no duplicate quotes were present
Verified and confirmed no missing values were present
Standardized column names to lowercase snake_case format
Removed extra whitespace from text fields
Removed the Tags: prefix and converted tags into comma-separated format
